---
title: "Blog 1"
date: ""
weight: 1
chapter: false
pre: " <b> 3.1. </b> "
---
# [**Mạng và Phân phối nội dung**](https://aws.amazon.com/blogs/networking-and-content-delivery/)

# **Triển khai quyền truy cập chi tiết Amazon Route 53 bằng khóa điều kiện AWS IAM (Phần 1\)**

Bởi Daniel Yu | vào 25/8/2025 |  trong mục [Networking & Content Delivery](https://aws.amazon.com/blogs/networking-and-content-delivery/category/networking-content-delivery/), [Security, Identity, & Compliance](https://aws.amazon.com/blogs/networking-and-content-delivery/category/security-identity-compliance/) | [Liên kết cố định](https://aws.amazon.com/blogs/networking-and-content-delivery/implementing-fine-grained-amazon-route-53-access-using-aws-iam-condition-keys-part-1/) | [Chia sẻ](https://aws.amazon.com/blogs/networking-and-content-delivery/implementing-fine-grained-amazon-route-53-access-using-aws-iam-condition-keys-part-1/#)

Các nhóm người dùng triển khai chiến lược đa tài khoản để hỗ trợ nhiều nhóm triển khai khối lượng công việc. Bài viết này dành cho các quản trị viên Amazon Web Services (AWS) và kỹ sư mạng — những người cần quản lý quyền truy cập DNS trên nhiều nhóm khi cùng sử dụng chung [Amazon Route 53 private hosted zone](https://docs.aws.amazon.com/Route53/latest/DeveloperGuide/hosted-zones-private.html) hoặc [public hosted zone](https://docs.aws.amazon.com/Route53/latest/DeveloperGuide/AboutHZWorkingWith.html). Có những tình huống mà nhiều nhóm chia sẻ cùng một hosted zone, và việc kiểm soát truy cập là cần thiết để cho phép hoặc từ chối cập nhật một hoặc nhiều bản ghi DNS trong hosted zone được chia sẻ. Một ví dụ là nhiều nhóm vận hành trong cùng subnet chia sẻ ([shared subnet](https://docs.aws.amazon.com/vpc/latest/userguide/vpc-sharing.html)) với chỉ một hosted zone chung, trong đó mỗi nhóm được ủy quyền quản lý một hậu tố (suffix) DNS cụ thể trong hosted zone đó. Một ví dụ khác là một hosted zone sandbox chung cho người dùng thử nghiệm, trong đó người dùng bị từ chối quyền quản lý các bản ghi DNS cho một số dịch vụ dùng chung trong hosted zone sandbox này.

Bài viết này thảo luận về một giải pháp có khả năng mở rộng để cấp quyền truy cập chi tiết vào các Route 53 hosted zone, private hoặc public, nhằm cấp quyền truy cập có điều kiện để cập nhật một tập con các bản ghi DNS trong một hosted zone được chia sẻ bằng cách sử dụng các khóa điều kiện của [AWS Identity and Access Management (IAM) condition keys](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_condition-keys.html) và [AWS principal tags](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_condition-keys.html#condition-keys-principaltag). Bài viết sẽ hướng dẫn bạn qua một ví dụ về cách cấp quyền truy cập chi tiết trong cùng một [tài khoản AWS](https://docs.aws.amazon.com/accounts/latest/reference/accounts-welcome.html) cho các [người dùng IAM (users)](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_users.html).

**Tổng quan giải pháp**

Chúng tôi giả định rằng bạn đã quen thuộc với [Route 53 hosted zones](https://docs.aws.amazon.com/Route53/latest/DeveloperGuide/hosted-zones-working-with.html) để quản lý DNS, [chính sách và quyền hạn IAM](https://docs.aws.amazon.com/IAM/latest/UserGuide/access_policies.html) để quản lý truy cập, và việc tạo các cặp khóa–giá trị (key-value pairs) như thuộc tính tùy chỉnh (custom attribute) bằng thẻ cho người dùng IAM ([IAM user tags](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_tags_users.html)). Giải pháp này sử dụng các chức năng của phần tử điều kiện IAM ([IAM condition element](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_elements_condition.html)) cùng với [Route53 IAM actions, resources, and conditions keys](https://docs.aws.amazon.com/service-authorization/latest/reference/list_amazonroute53.html) để thực hiện kiểm soát truy cập chi tiết (fine-grained access) đối với các Route 53 hosted zone. Thành phần IAM policy **condition** là một yếu tố tùy chọn trong một policy statement, xác định các điều kiện mà tại đó chính sách sẽ cấp hoặc từ chối quyền truy cập. Giải pháp này đơn giản hóa việc quản lý truy cập bằng cách cho phép bạn tạo các quyền chi tiết dựa trên thuộc tính người dùng và giảm quyền hạn nguyên tắc xuống theo nguyên tắc least-privilege.

Sơ đồ sau minh họa kiến trúc truy cập chi tiết của Route 53\. Sơ đồ cho thấy người dùng IAM (bên trái) được gán thẻ tùy chỉnh (custom tag) với khóa “ *dnsrecords* ” và giá trị là các bản ghi DNS mà họ được phép cập nhật. Khi người dùng cố gắng sửa đổi bản ghi DNS trong Route 53 hosted zone (bên phải), chính sách IAM (ở giữa) sẽ đánh giá hành động [route53:ChangeResourceRecordSets](https://docs.aws.amazon.com/service-authorization/latest/reference/list_amazonroute53.html#amazonroute53-actions-as-permissions) và so sánh tên bản ghi DNS mà người dùng muốn cập nhật với giá trị của thẻ người dùng bằng cách sử dụng khóa điều kiện [route53:ChangeResourceRecordSetsNormalizedRecordNames](https://docs.aws.amazon.com/service-authorization/latest/reference/list_amazonroute53.html#amazonroute53-policy-keys) để quyết định có cấp quyền truy cập hay không.

## **![][image1]**

  *Hình 1: Truy cập chi tiết Route 53 bằng IAM condition keys*

Bốn chính sách quyền sau đây cho thấy việc sử dụng bốn toán tử điều kiện để cấp quyền cho các bản ghi DNS. Khóa điều kiện route53:ChangeResourceRecordSetsNormalizedRecordNames  kiểm soát các tên bản ghi DNS trong yêu cầu hành động route53:ChangeResourceRecordSets bằng cách so khớp với khóa ${aws:PrincipalTag/{custom-attribute}} để cấp quyền quản lý bản ghi DNS cụ thể. Khóa điều kiện ${aws:PrincipalTag/{custom-attribute}} chỉ định giá trị thẻ được gắn với IAM user.

## **Cho phép truy cập vào bản ghi DNS cụ thể bằng StringEquals**

Sử dụng toán tử ForAllValues:StringEquals khi bạn muốn cấp quyền quản lý một tên bản ghi DNS cụ thể. Cách tiếp cận này lý tưởng khi bạn muốn giới hạn người dùng chỉ được quản lý chính xác bản ghi đã xác định mà không có quyền truy cập vào các bản ghi khác trong hosted zone chung.

Chính sách quyền sau (thay *{custom-attribute}*  và *{Route53HostedZoneID}*bằng thuộc tính thẻ tùy chỉnh và ID hosted zone của bạn) cho phép cập nhật một bản ghi DNS duy nhất:
``
| {"Version": "2012-10-17",    "Statement": \[        {            "Effect": "Allow",            "Action": "route53:ChangeResourceRecordSets",            "Resource": "arn:aws:route53:::hostedzone/{Route53HostedZoneID}",            "Condition": {                "ForAllValues:StringEquals": {                    "route53:ChangeResourceRecordSetsNormalizedRecordNames": \[                        "${aws:PrincipalTag/{custom-attribute}}"                    \]                }            }        }    \]} |
| :---- |
``
Chính sách này cùng với giá trị thẻ là “ svc1.example.com ” có nghĩa là người dùng chỉ có thể quản lý bản ghi DNS “svc1.example.com”.  
 Người dùng sẽ bị từ chối quyền đối với các bản ghi khác, ví dụ:

* Tạo bản ghi mới “ api.svc1.example.com ”

* Cập nhật bản ghi hiện có “marketing.example.com”

* Xóa bản ghi hiện có “ svc2.example.com ”

## **Từ chối truy cập vào bản ghi DNS cụ thể bằng StringNotEquals**

Sử dụng toán tử ForAllValues:StringNotEquals khi bạn muốn từ chối quyền quản lý một bản ghi DNS cụ thể. Cách tiếp cận này lý tưởng khi bạn muốn bảo vệ một bản ghi DNS cụ thể trong khi người dùng vẫn có thể tạo hoặc quản lý các bản ghi khác trong hosted zone chung.

Chính sách quyền sau (thay *{custom-attribute}* và *{Route53HostedZoneID}* bằng thuộc tính thẻ tùy chỉnh và ID hosted zone của bạn) sẽ từ chối cập nhật một bản ghi DNS duy nhất:
``
| {    "Version": "2012-10-17",    "Statement": \[        {            "Effect": "Allow",            "Action": "route53:ChangeResourceRecordSets",            "Resource": "arn:aws:route53:::hostedzone/{Route53HostedZoneID}",            "Condition": {                "ForAllValues:StringNotEquals": {                    "route53:ChangeResourceRecordSetsNormalizedRecordNames": \[                        "${aws:PrincipalTag/{custom-attribute}}"                    \]                }            }        }    \]} |
| :---- |
``
Chính sách này cùng với giá trị thẻ là svc1.example.comcó nghĩa là người dùng sẽ bị từ chối quyền quản lý bản ghi DNS “svc1.example.com”.  
 Người dùng vẫn được phép cập nhật các bản ghi DNS khác, ví dụ:

* Tạo bản ghi mới “api.svc1.example.com”

* Cập nhật bản ghi hiện có “marketing.example.com”

* Xóa bản ghi hiện có “svc2.example.com”

## **Cho phép truy cập vào các bản ghi DNS kết thúc với mẫu bằng StringLike**

Sử dụng toán tử ForAllValues:StringLikevới ký tự đại diện “\*” và dấu chấm “.” phía trước thuộc tính tùy chỉnh để cấp quyền quản lý các bản ghi DNS trong một hậu tố tên miền.  
 Cách tiếp cận này lý tưởng khi bạn muốn giới hạn người dùng chỉ quản lý một hậu tố tên miền mà không được phép truy cập các bản ghi khác trong hosted zone chung.

Chính sách quyền sau (thay *{custom-attribute}* và *{Route53HostedZoneID}* bằng thuộc tính thẻ tùy chỉnh và ID hosted zone của bạn) cho phép cập nhật các bản ghi DNS trong hậu tố tên miền:
``
| {    "Version": "2012-10-17",    "Statement": \[        {            "Effect": "Allow",            "Action": "route53:ChangeResourceRecordSets",            "Resource": "arn:aws:route53:::hostedzone/{Route53HostedZoneID}",            "Condition": {                "ForAllValues:StringLike": {                    "route53:ChangeResourceRecordSetsNormalizedRecordNames": \[                        "\*.${aws:PrincipalTag/{custom-attribute}}"                    \]                }            }        }    \]} |
| :---- |
``
Chính sách này cùng với giá trị thẻ là svc1.example.comcó nghĩa là người dùng có thể quản lý bất kỳ bản ghi DNS nào trong hậu tố “.svc1.example.com”, ví dụ:

* Tạo bản ghi mới “api.svc1.example.com”

* Cập nhật bản ghi hiện có “dev.svc1.example.com”

* Xóa bản ghi hiện có “prod.svc1.example.com”

Tuy nhiên, người dùng tương tự sẽ bị từ chối quyền với các bản ghi khác, ví dụ:

* Tạo bản ghi mới “svc1.example.com”

* Cập nhật bản ghi hiện có “marketing.example.com”

* Xóa bản ghi hiện có “[api.svc2.example.com](http://api.svc2.example.com)”

## **Từ chối truy cập vào các bản ghi DNS kết thúc với mẫu bằng StringNotLike**

Sử dụng toán tử ForAllValues:StringNotLike với ký tự đại diện “\*” và dấu chấm “.” phía trước thuộc tính tùy chỉnh để từ chối cập nhật các bản ghi DNS trong hậu tố tên miền.  
 Cách tiếp cận này lý tưởng khi bạn muốn bảo vệ một hậu tố DNS cụ thể trong môi trường chia sẻ, trong khi người dùng vẫn được phép tạo bất kỳ bản ghi DNS nào khác trong hosted zone chung.

Chính sách quyền sau (thay *{custom-attribute}* và *{Route53HostedZoneID}* bằng thuộc tính thẻ tùy chỉnh và ID hosted zone của bạn) từ chối cập nhật các bản ghi DNS kết thúc bằng mẫu cụ thể:
``
| {    "Version": "2012-10-17",    "Statement": \[        {            "Effect": "Allow",            "Action": "route53:ChangeResourceRecordSets",            "Resource": "arn:aws:route53:::hostedzone/{Route53HostedZoneID}",            "Condition": {                "ForAllValues:StringNotLike": {                    "route53:ChangeResourceRecordSetsNormalizedRecordNames": \[                        "\*.${aws:PrincipalTag/{custom-attribute}}"                    \]                }            }        }    \]} |
| :---- |
``
Chính sách này cùng với giá trị thẻ là svc1.example.comcó nghĩa là người dùng sẽ bị từ chối quyền quản lý các bản ghi DNS trong hậu tố “.svc1.example.com”, ví dụ:

* Tạo bản ghi mới “api.svc1.example.com”

* Cập nhật bản ghi hiện có “dev.svc1.example.com”

* Xóa bản ghi hiện có “prod.svc1.example.com”

Tuy nhiên, người dùng tương tự sẽ được phép với các bản ghi khác, ví dụ:

* Tạo bản ghi mới “svc1.example.com”

* Cập nhật bản ghi hiện có “marketing.example.com”

* Xóa bản ghi hiện có “api.svc2.example.com

## **Triển khai giải pháp**

Bạn tạo một giải pháp cho phép người dùng chỉ quản lý các bản ghi DNS khớp với giá trị thẻ được gán cho họ. Các bước sau cho phép bạn cấu hình thẻ người dùng IAM và chính sách để bật kiểm soát truy cập chi tiết cho Route 53 hosted zone của mình. Khi hoàn tất, người dùng chỉ có thể quản lý các bản ghi DNS khớp với giá trị trong thẻ tùy chỉnh của họ.

Ví dụ này sử dụng giá trị trong thuộc tính tùy chỉnh “dnsrecords” để cấp quyền truy cập có điều kiện cho việc cập nhật các bản ghi DNS kết thúc bằng hậu tố tên miền “.svc1.example.com” trong shared hosted zone “example.com” bằng một chính sách quyền trong cùng tài khoản.

### **Điều kiện tiên quyết**

Trước khi thực hiện, bạn cần có:

* Hosted zone cho tên miền “example.com”

* IAM user trong cùng tài khoản AWS với hosted zone

* Đăng nhập vào tài khoản AWS của hosted zone với quyền cập nhật IAM users và permissions

### **Bước 1: Tạo principal tag**

Sử dụng các bước trong “[tag IAM users](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_tags_users.html)”, tạo thuộc tính/thẻ “dnsrecords” với giá trị “svc1.example.com” cho IAM users trong [AWS Management Console](https://aws.amazon.com/console/).

Bạn có thể dùng AWS CLI sau để tạo khóa “dnsrecords” với giá trị “svc1.example.com”, thay \<USER\_NAME\> bằng tên IAM user của bạn:
``
aws iam tag-user \--user-name \<USER\_NAME\> \--tags '{"Key": "dnsrecord", "Value": "svc1.example.com"}'
``
### **Bước 2: Tạo permission policy**

Sử dụng hướng dẫn “[Define custom IAM permissions with customer managed policies](https://docs.aws.amazon.com/IAM/latest/UserGuide/access_policies_create.html)” để tạo chính sách quyền IAM bằng tệp JSON sau trong console.  
 Có ký tự đại diện “\*” và dấu chấm “.” phía trước ${aws:PrincipalTag/dnsrecords} để bật so khớp chuỗi.  
 Giá trị *Z1R8UBAEXAMPLE* là ID của private hosted zone và bạn phải thay thế bằng hosted zone của mình.
``
| {    "Version": "2012-10-17",    "Statement": \[        {            "Effect": "Allow",            "Action": "route53:ChangeResourceRecordSets",            "Resource": "arn:aws:route53:::hostedzone/Z1R8UBAEXAMPLE",            "Condition": {                "ForAllValues:StringLike": {                    "route53:ChangeResourceRecordSetsNormalizedRecordNames": \[                        "\*.${aws:PrincipalTag/dnsrecords}"                    \]                }            }        }    \]} |
| :---- |
``
Bạn có thể dùng CLI để tạo chính sách quyền, thay \<POLICY\_NAME\> bằng tên chính sách và \<DOCUMENT\_FILE\>  bằng đường dẫn tệp JSON ở trên:
``
| aws iam create-policy \-policy-name \<POLICY\_NAME\> \--policy-document \<DOCUMENT\_FILE\> |
| :---- |
``
### **Bước 3: Gắn chính sách quyền cho IAM user hoặc group**

Gắn chính sách quyền đã tạo ở Bước 2 cho người dùng IAM có gán custom tag ở Bước 1, hoặc cho nhóm (group) chứa người dùng đó để bật kiểm soát truy cập chi tiết (fine-grained access control) vào hosted zone cho người dùng.

Thực hiện theo các bước trong [Changing permissions for an IAM user](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_users_change-permissions.html) để gắn quyền cho người dùng, hoặc theo [Attach a policy to an IAM](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_groups_manage_attach-policy.html) user group để gắn quyền cho nhóm trong console.

Bạn có thể sử dụng lệnh CLI sau để gắn chính sách quyền (permission policy) cho người dùng IAM, thay \<POLICY\_ARN\>bằng ARN của chính sách đã tạo ở Bước 2 và `<USER_NAME>` bằng tên người dùng IAM đã tạo ở Bước 1:
``
| aws iam attach-user-policy \--policy-arn \<POLICY\_ARN\> \--user-name \<USER\_NAME\> |
| :---- |
``
Bạn có thể sử dụng lệnh CLI sau để gắn chính sách quyền (permission policy) cho nhóm IAM, thay `<POLICY_ARN>` bằng ARN của chính sách đã tạo ở Bước 2 và `<GROUP_NAME>` bằng tên nhóm chứa người dùng IAM đã tạo ở Bước 1:  
aws iam attach-user-policy \--policy-arn \<POLICY\_ARN\> \--group-name \<GROUP\_NAME\>

### **Bước 4: Xác minh quyền cập nhật DNS**

IAM user hiện có quyền quản lý các bản ghi DNS trong hậu tố tên miền “.svc1.example.com” của shared hosted zone “example.com”.  
 Bạn có thể xác minh quyền này hoạt động đúng bằng cách sử dụng các bước trong Developer Guide [Route 53 console](https://docs.aws.amazon.com/Route53/latest/DeveloperGuide/resource-record-sets-editing.html) hoặc [CLI command change-resource-record-sets](https://docs.aws.amazon.com/Route53/latest/DeveloperGuide/route-53_example_route-53_ChangeResourceRecordSets_section.html).

Ví dụ, lệnh sau để tạo bản ghi “dev.svc1.example.com” sẽ thành công:
``
| aws route53 change-resource-record-sets \--hosted-zone-id Z1R8UBAEXAMPLE \--change-batch file://svc1\-create.json |
| :---- |
``
``
{  
    "Comment": "configuration to create dev.svc1.example.com record",  
    "Changes": \[  
        {  
            "Action": "CREATE",  
            "ResourceRecordSet": {  
                "Name": "dev.svc1.example.com",  
                "Type": "A",  
                "TTL": 300,  
                "ResourceRecords": \[  
                    {  
                        "Value": "10.1.1.1"  
                    }  
                \]  
            }  
        }  
    \]  
}  

``
Lệnh sau để tạo bản ghi “dev.svc2.example.com” sẽ **thất bại**:
``
| aws route53 change-resource-record-sets \--hosted-zone-id Z1R8UBAEXAMPLE \--change-batch file://svc2\-create.json |
| :---- |
``

``
{  
    "Comment": "configuration to create dev.svc2.example.com record",  
    "Changes": \[  
        {  
            "Action": "CREATE",  
            "ResourceRecordSet": {  
                "Name": "dev.svc2.example.com",  
                "Type": "A",  
                "TTL": 300,  
                "ResourceRecords": \[  
                    {  
                        "Value": "10.1.1.1"  
                    }  
               \]  
            }  
        }  
    \]  
}
``
## **Các lưu ý**

Mặc dù khóa điều kiện route53:ChangeResourceRecordSetsNormalizedRecordNames là một khóa có nhiều giá trị và có thể so khớp với nhiều giá trị bằng dấu phẩy “,”, nhưng giá trị tag không thể chứa dấu phẩy “,” để phân tách nhiều giá trị.Do đó, thuộc tính tùy chỉnh chỉ có thể chứa một giá trị bản ghi DNS để hoạt động với chính sách quyền. Nếu cần kiểm soát truy cập cho nhiều giá trị bản ghi DNS, bạn phải sử dụng nhiều thuộc tính tùy chỉnh tương ứng với các chính sách quyền riêng biệt.

Nhiều khóa [điều kiện IAM khác cho Route 53](https://docs.aws.amazon.com/Route53/latest/DeveloperGuide/specifying-conditions-route53.html) có sẵn để mở rộng kiểm soát truy cập đối với bản ghi DNS. Thao tác route53:ChangeResourceRecordSetsActionscó thể giới hạn hành động ở các thao tác CREATE, UPDATE, và DELETE. Thao tác route53:ChangeResourceRecordSetsRecordTypes có thể giới hạn hành động theo loại bản ghi DNS.

Khi quản lý quyền IAM, hãy xem xét các [IAM quotas và giới hạn ký tự](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_iam-quotas.html) cho users, groups, và policies.

Nếu quyền của bạn không hoạt động như mong đợi, tài liệu [Troubleshoot IAM Policies](https://docs.aws.amazon.com/IAM/latest/UserGuide/troubleshoot_policies.html) bao gồm các hướng dẫn hữu ích cho các vấn đề thường gặp.

Đối với các môi trường không sử dụng shared hosted zones, nơi mỗi nhóm quản lý private hosted zones riêng cho dịch vụ của họ, [Route 53 Profiles](https://docs.aws.amazon.com/Route53/latest/DeveloperGuide/profiles.html) là thực tiễn tốt nhất được khuyến nghị để quản lý tập trung các cấu hình DNS cho [Amazon Virtual Private Clouds (Amazon VPCs)](https://docs.aws.amazon.com/vpc/latest/userguide/what-is-amazon-vpc.html) và các tài khoản.  
 Bài viết [Using Amazon Route 53 Profiles for scalable multi-account AWS environments](https://aws.amazon.com/blogs/networking-and-content-delivery/using-amazon-route-53-profiles-for-scalable-multi-account-aws-environments/) trình bày kiến trúc này.

## **Kết luận**

Trong bài viết này, chúng ta đã xem xét một giải pháp có khả năng mở rộng bằng cách sử dụng AWS IAM condition keys và AWS principal tags để kiểm soát truy cập chi tiết cho các Amazon Route 53 hosted zones được chia sẻ, cho phép nhiều nhóm quản lý các tập con bản ghi DNS trong một hosted zone chung.Phần này bao gồm ví dụ triển khai quyền truy cập có điều kiện trong cùng một tài khoản.Trong hai bài viết tiếp theo, chúng tôi sẽ xem xét quyền truy cập chi tiết cross-account và federated user với IAM condition keys và AWS principal tags.

## **Về tác giả**

| Daniel Yu Daniel Yu là Senior Technical Account Manager, hợp tác với khách hàng Enterprise Support để tối ưu hóa sáng kiến chuyển đổi đám mây của họ. Với chuyên môn về hạ tầng mạng và bảo mật, anh chuyên cung cấp hướng dẫn chiến lược về thiết kế kiến trúc AWS và vận hành xuất sắc. |
| :---- |

[image1]: <data:image/png;base64,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>