---
title: "Implementing Fine-Grained Amazon Route 53 Access Using AWS IAM Condition Keys (Part 1)"
date: ""
weight: 1
chapter: false
pre: " <b> 3.1. </b> "
---

# Networking & Content Delivery

# Implementing Fine-Grained Amazon Route 53 Access Using AWS IAM Condition Keys (Part 1)

By Daniel Yu | 25 Aug 2025 | Networking & Content Delivery, Security, Identity, & Compliance

Many organizations adopt a multi-account strategy to support multiple deployment teams. This article is for AWS administrators and network engineers managing DNS access across teams that share an Amazon Route 53 hosted zone (private or public). In shared hosted-zone scenarios, teams often need controlled permissions to allow or deny updates to specific DNS records.

This post describes a scalable pattern to grant fine-grained access to Route 53 hosted zones using IAM condition keys and principal tags. The example shows how to allow conditional updates to a subset of DNS records in the same AWS account by comparing requested record names against values stored in IAM principal tags.

Solution overview

We assume familiarity with Route 53 hosted zones, IAM policies, and IAM user tags. The design uses the policy `Condition` element with Route 53 condition keys (for example `route53:ChangeResourceRecordSetsNormalizedRecordNames`) and `${aws:PrincipalTag/<key>}` to compare requested record names with the tag value attached to the IAM principal. That comparison enables least-privilege updates to record names or suffixes.

Architecture

IAM users receive a custom principal tag (for example `dnsrecords`) whose value is either a single FQDN (e.g., `svc1.example.com`) or a suffix. A policy evaluates `route53:ChangeResourceRecordSets` and uses `route53:ChangeResourceRecordSetsNormalizedRecordNames` to compare the requested record names with the user tag.

Allow a specific DNS record (ForAllValues:StringEquals)

Use `ForAllValues:StringEquals` to permit modifications only when the requested record name exactly equals the tag value. Example (replace `{custom-attribute}` and `{Route53HostedZoneID}`):

```
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Action": "route53:ChangeResourceRecordSets",
      "Resource": "arn:aws:route53:::hostedzone/{Route53HostedZoneID}",
      "Condition": {
        "ForAllValues:StringEquals": {
          "route53:ChangeResourceRecordSetsNormalizedRecordNames": [
            "${aws:PrincipalTag/{custom-attribute}}"
          ]
        }
      }
    }
  ]
}
```

If the tag value is `svc1.example.com`, the user can only manage that record.

Deny a specific DNS record (ForAllValues:StringNotEquals)

Use `ForAllValues:StringNotEquals` to deny updates for a specific record while allowing other changes:

```
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Action": "route53:ChangeResourceRecordSets",
      "Resource": "arn:aws:route53:::hostedzone/{Route53HostedZoneID}",
      "Condition": {
        "ForAllValues:StringNotEquals": {
          "route53:ChangeResourceRecordSetsNormalizedRecordNames": [
            "${aws:PrincipalTag/{custom-attribute}}"
          ]
        }
      }
    }
  ]
}
```

Allow a domain suffix (ForAllValues:StringLike)

Use `ForAllValues:StringLike` with a wildcard to permit updates within a suffix (e.g., `*.svc1.example.com`):

```
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Action": "route53:ChangeResourceRecordSets",
      "Resource": "arn:aws:route53:::hostedzone/{Route53HostedZoneID}",
      "Condition": {
        "ForAllValues:StringLike": {
          "route53:ChangeResourceRecordSetsNormalizedRecordNames": [
            "*.${aws:PrincipalTag/{custom-attribute}}"
          ]
        }
      }
    }
  ]
}
```

Prerequisites and notes

- Principal tag values must not contain commas; a single tag supports a single DNS value. To enable multiple allowed values, use multiple tags and policies.
- Replace `{Route53HostedZoneID}` and `{custom-attribute}` with your actual hosted zone ID and tag key (for example `dnsrecords`).
- Workflow: tag IAM users, create the managed policy with the condition keys, attach the policy to users/groups, and verify changes using the Route 53 console or CLI.

Example tag command (replace `<USER_NAME>`):

```
aws iam tag-user --user-name <USER_NAME> --tags Key=dnsrecords,Value=svc1.example.com
```

This pattern simplifies access control for shared hosted zones by using principal tags and condition keys to implement least-privilege DNS management. Part 2 will cover cross-account and federated-user scenarios.
