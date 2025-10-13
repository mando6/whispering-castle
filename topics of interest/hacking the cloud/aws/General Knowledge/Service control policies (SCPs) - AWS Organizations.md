---
title: "Service control policies (SCPs) - AWS Organizations"
source: "https://docs.aws.amazon.com/organizations/latest/userguide/orgs_manage_policies_scps.html"
author:
  - "[[Authorization policies]]"
published:
created: 2025-06-06
description: "Service control policies (SCPs) offer central control over the maximum available permissions for IAM users and IAM roles in an organization."
tags:
  - "clippings"
---
Service control policies (SCPs) - AWS Organizations

[Testing effects of SCPs](https://docs.aws.amazon.com/organizations/latest/userguide/#scp-warning-testing-effect) [Maximum size of SCPs](https://docs.aws.amazon.com/organizations/latest/userguide/#scp-size-limit) [Attaching SCPs to different levels in the organization](https://docs.aws.amazon.com/organizations/latest/userguide/#scp-about-inheritance) [SCP effects on permissions](https://docs.aws.amazon.com/organizations/latest/userguide/#scp-effects-on-permissions) [Using access data to improve SCPs](https://docs.aws.amazon.com/organizations/latest/userguide/#data-from-iam) [Tasks and entities not restricted by SCPs](https://docs.aws.amazon.com/organizations/latest/userguide/#not-restricted-by-scp)

Service control policies (SCPs) are a type of organization policy that you can use to manage permissions in your organization. SCPs offer central control over the maximum available permissions for the IAM users and IAM roles in your organization. SCPs help you to ensure your accounts stay within your organization’s access control guidelines. SCPs are available only in an organization that has [all features enabled](https://docs.aws.amazon.com/organizations/latest/userguide/orgs_manage_org_support-all-features.html). SCPs aren't available if your organization has enabled only the consolidated billing features. For instructions on enabling SCPs, see [Enabling a policy type](https://docs.aws.amazon.com/organizations/latest/userguide/enable-policy-type.html).

SCPs do not grant permissions to the IAM users and IAM roles in your organization. No permissions are granted by an SCP. An SCP defines a permission guardrail, or sets limits, on the actions that the IAM users and IAM roles in your organization can perform. To grant permissions, the administrator must attach policies to control access, such as identity-based policies that are attached to IAM users and IAM roles, and resource-based policies that are attached to the resources in your accounts. For more information, see [Identity-based policies and resource-based policies](https://docs.aws.amazon.com/IAM/latest/UserGuide/access_policies_identity-vs-resource.html) in the *IAM User Guide*.

The [effective permissions](https://docs.aws.amazon.com/organizations/latest/userguide/#scp-effects-on-permissions) are the logical intersection between what is allowed by the SCP and [resource control policies (RCPs)](https://docs.aws.amazon.com/organizations/latest/userguide/orgs_manage_policies_rcps.html) and what is allowed by the identity-based and resource-based policies.

###### SCPs don't affect users or roles in the management account

SCPs don't affect users or roles in the management account. They affect only the member accounts in your organization. This also means that SCPs apply to member accounts that are designated as delegated administrators.

###### Topics

- [Testing effects of SCPs](https://docs.aws.amazon.com/organizations/latest/userguide/#scp-warning-testing-effect)
- [Maximum size of SCPs](https://docs.aws.amazon.com/organizations/latest/userguide/#scp-size-limit)
- [Attaching SCPs to different levels in the organization](https://docs.aws.amazon.com/organizations/latest/userguide/#scp-about-inheritance)
- [SCP effects on permissions](https://docs.aws.amazon.com/organizations/latest/userguide/#scp-effects-on-permissions)
- [Using access data to improve SCPs](https://docs.aws.amazon.com/organizations/latest/userguide/#data-from-iam)
- [Tasks and entities not restricted by SCPs](https://docs.aws.amazon.com/organizations/latest/userguide/#not-restricted-by-scp)
- [SCP evaluation](https://docs.aws.amazon.com/organizations/latest/userguide/orgs_manage_policies_scps_evaluation.html)
- [SCP syntax](https://docs.aws.amazon.com/organizations/latest/userguide/orgs_manage_policies_scps_syntax.html)
- [Service control policy examples](https://docs.aws.amazon.com/organizations/latest/userguide/orgs_manage_policies_scps_examples.html)
- [Troubleshooting service control policies (SCPs) with AWS Organizations](https://docs.aws.amazon.com/organizations/latest/userguide/org_troubleshoot_policies.html)

## Testing effects of SCPs

AWS strongly recommends that you don't attach SCPs to the root of your organization without thoroughly testing the impact that the policy has on accounts. Instead, create an OU that you can move your accounts into one at a time, or at least in small numbers, to ensure that you don't inadvertently lock users out of key services. One way to determine whether a service is used by an account is to examine the [service last accessed data in IAM](https://docs.aws.amazon.com/IAM/latest/UserGuide/access_policies_access-advisor.html). Another way is to [use AWS CloudTrail to log service usage at the API level](https://docs.aws.amazon.com/awscloudtrail/latest/userguide/how-cloudtrail-works.html).

###### Note

You should not remove the **FullAWSAccess** policy unless you modify or replace it with a separate policy with allowed actions, otherwise all AWS actions from member accounts will fail.

## Maximum size of SCPs

All characters in your SCP count against its [maximum size](https://docs.aws.amazon.com/organizations/latest/userguide/orgs_reference_limits.html#min-max-values). The examples in this guide show the SCPs formatted with extra white space to improve their readability. However, to save space if your policy size approaches the maximum size, you can delete any white space, such as space characters and line breaks that are outside quotation marks.

###### Tip

Use the visual editor to build your SCP. It automatically removes extra white space.

## Attaching SCPs to different levels in the organization

For a detailed explanation of how SCPs work, see [SCP evaluation](https://docs.aws.amazon.com/organizations/latest/userguide/orgs_manage_policies_scps_evaluation.html).

## SCP effects on permissions

SCPs are similar to AWS Identity and Access Management permission policies and use almost the same syntax. However, an SCP never grants permissions. Instead, SCPs are access controls that specify the maximum available permissions for the IAM users and IAM roles in your organization. For more information, see [Policy Evaluation Logic](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_evaluation-logic.html) in the *IAM User Guide*.

- SCPs ***affect only IAM users and roles*** that are managed by accounts that are part of the organization. SCPs don't affect resource-based policies directly. They also don't affect users or roles from accounts outside the organization. For example, consider an Amazon S3 bucket that's owned by account A in an organization. The bucket policy (a resource-based policy) grants access to users from account B outside the organization. Account A has an SCP attached. That SCP doesn't apply to those outside users in account B. The SCP applies only to users that are managed by account A in the organization.
- An SCP restricts permissions for IAM users and roles in member accounts, including the member account's root user. Any account has only those permissions permitted by ***every*** parent above it. If a permission is blocked at any level above the account, either implicitly (by not being included in an `Allow` policy statement) or explicitly (by being included in a `Deny` policy statement), a user or role in the affected account can't use that permission, even if the account administrator attaches the `AdministratorAccess` IAM policy with \*/\* permissions to the user.
- SCPs affect only ***member*** accounts in the organization. They have no effect on users or roles in the management account. This also means that SCPs apply to member accounts that are designated as delegated administrators. For more information, see [Best practices for the management account](https://docs.aws.amazon.com/organizations/latest/userguide/orgs_best-practices_mgmt-acct.html).
- Users and roles must still be granted permissions with appropriate IAM permission policies. A user without any IAM permission policies has no access, even if the applicable SCPs allow all services and all actions.
- If a user or role has an IAM permission policy that grants access to an action that is also allowed by the applicable SCPs, the user or role can perform that action.
- If a user or role has an IAM permission policy that grants access to an action that is either not allowed or explicitly denied by the applicable SCPs, the user or role can't perform that action.
- SCPs affect all users and roles in attached accounts, ***including the root user***. The only exceptions are those described in [Tasks and entities not restricted by SCPs](https://docs.aws.amazon.com/organizations/latest/userguide/#not-restricted-by-scp).
- SCPs ***do not*** affect any service-linked role. Service-linked roles enable other AWS services to integrate with AWS Organizations and can't be restricted by SCPs.
- When you disable the SCP policy type in a root, all SCPs are automatically detached from all AWS Organizations entities in that root. AWS Organizations entities include organizational units, organizations, and accounts. If you reenable SCPs in a root, that root reverts to only the default `FullAWSAccess` policy automatically attached to all entities in the root. Any attachments of SCPs to AWS Organizations entities from before SCPs were disabled are lost and aren't automatically recoverable, although you can manually reattach them.
- If both a permissions boundary (an advanced IAM feature) and an SCP are present, then the boundary, the SCP, and the identity-based policy must all allow the action.

## Using access data to improve SCPs

When signed in with management account credentials, you can view [service last accessed data](https://docs.aws.amazon.com/IAM/latest/UserGuide/access_policies_access-advisor.html) for an AWS Organizations entity or policy in the **AWS Organizations** section of the IAM console. You can also use the AWS Command Line Interface (AWS CLI) or AWS API in IAM to retrieve service last accessed data. This data includes information about which allowed services that the IAM users and roles in an AWS Organizations account last attempted to access and when. You can use this information to identify unused permissions so that you can refine your SCPs to better adhere to the principle of [least privilege](https://docs.aws.amazon.com/IAM/latest/UserGuide/best-practices.html#grant-least-privilege).

For example, you might have a [deny list SCP](https://docs.aws.amazon.com/organizations/latest/userguide/orgs_manage_policies_scps_evaluation.html#how_scps_deny) that prohibits access to three AWS services. All services that aren't listed in the SCP's `Deny` statement are allowed. The service last accessed data in IAM tells you which AWS services are allowed by the SCP but are never used. With that information, you can update the SCP to deny access to services that you don't need.

For more information, see the following topics in the *IAM User Guide*:

- [Viewing Organizations Service Last Accessed Data for Organizations](https://docs.aws.amazon.com/IAM/latest/UserGuide/access_policies_access-advisor-view-data-orgs.html)
- [Using Data to Refine Permissions for an Organizational Unit](https://docs.aws.amazon.com/IAM/latest/UserGuide/access_policies_access-advisor-example-scenarios.html#access_policies_access-advisor-reduce-permissions-orgs)

## Tasks and entities not restricted by SCPs

You ***can't*** use SCPs to restrict the following tasks:

- Any action performed by the management account
- Any action performed using permissions that are attached to a service-linked role
- Register for the Enterprise support plan as the root user
- Provide trusted signer functionality for CloudFront private content
- Configure reverse DNS for an Amazon Lightsail email server and Amazon EC2 instance as the root user
- Tasks on some AWS-related services:
	- Alexa Top Sites
	- Alexa Web Information Service
	- Amazon Mechanical Turk
	- Amazon Product Marketing API

---

Organizations › userguide

![](https://prod.us-west-2.tcx-beacon.docs.aws.dev/recommendation-beacon/similar/impressions/7f4b136c-a690-46a1-9bf6-452dd24e3df6/kp-FBYufpG4MvmFmgUJ3RAuQY_HDlBxA-144JrwfX-HeqjKnMdLciA==/https:%7C%7Cdocs.aws.amazon.com%7Corganizations%7Clatest%7Cuserguide%7Corgs_manage_policies_scps.html/https:%7C%7Cdocs.aws.amazon.com%7Corganizations%7Clatest%7Cuserguide%7Corgs_manage_policies_rcps.html)

Resource control policies restrict maximum permissions for resources in organization member accounts, setting guardrails on actions identities can take.

*March 5, 2025*

Step-functions › dg

![](https://prod.us-west-2.tcx-beacon.docs.aws.dev/recommendation-beacon/similar/impressions/7f4b136c-a690-46a1-9bf6-452dd24e3df6/kp-FBYufpG4MvmFmgUJ3RAuQY_HDlBxA-144JrwfX-HeqjKnMdLciA==/https:%7C%7Cdocs.aws.amazon.com%7Corganizations%7Clatest%7Cuserguide%7Corgs_manage_policies_scps.html/https:%7C%7Cdocs.aws.amazon.com%7Cstep-functions%7Clatest%7Cdg%7Csecurity_iam_id-based-policy-examples.html)

IAM policies grant permissions to create, access, or delete Step Functions resources. Least-privilege permissions, multi-factor authentication, and IAM Access Analyzer ensure secure access.

*February 27, 2025*

### Discover highly rated pages

Abstracts generated by AI

Organizations › userguide

![](https://prod.us-west-2.tcx-beacon.docs.aws.dev/recommendation-beacon/highlyRated/impressions/7f4b136c-a690-46a1-9bf6-452dd24e3df6/kp-FBYufpG4MvmFmgUJ3RAuQY_HDlBxA-144JrwfX-HeqjKnMdLciA==/https:%7C%7Cdocs.aws.amazon.com%7Corganizations%7Clatest%7Cuserguide%7Corgs_manage_policies_scps.html/https:%7C%7Cdocs.aws.amazon.com%7Corganizations%7Clatest%7Cuserguide%7Corgs_introduction.html)

AWS Organizations centrally manages AWS resources, groups accounts into organizational units, applies policies for governance, shares resources across accounts, provides centralized billing, automates account creation, and enforces security compliance.

*February 28, 2025*

Organizations › userguide

![](https://prod.us-west-2.tcx-beacon.docs.aws.dev/recommendation-beacon/highlyRated/impressions/7f4b136c-a690-46a1-9bf6-452dd24e3df6/kp-FBYufpG4MvmFmgUJ3RAuQY_HDlBxA-144JrwfX-HeqjKnMdLciA==/https:%7C%7Cdocs.aws.amazon.com%7Corganizations%7Clatest%7Cuserguide%7Corgs_manage_policies_scps.html/https:%7C%7Cdocs.aws.amazon.com%7Corganizations%7Clatest%7Cuserguide%7Corgs_getting-started_concepts.html)

AWS Organizations centrally manages accounts, policies, and configurations across an organization. Responsibilities include grouping accounts into organizational units, applying service control and resource control policies, configuring declarative policies, and managing backup policies.

*March 20, 2025*

[Provide feedback](https://docs.aws.amazon.com/forms/aws-doc-feedback?hidden_service_name=Organizations&topic_url=https://docs.aws.amazon.com/en_us/organizations/latest/userguide/orgs_manage_policies_scps.html)