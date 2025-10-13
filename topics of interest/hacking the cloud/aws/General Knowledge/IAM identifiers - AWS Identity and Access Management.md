---
title: "IAM identifiers - AWS Identity and Access Management"
source: "https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_identifiers.html#identifiers-unique-ids"
author:
  - "[[SetContext]]"
published:
created: 2025-06-06
description: "Describes resource names (friendly names, identifiers, unique IDs, paths, and ARNs) for AWS Identity and Access Management (IAM) resources such as users, IAM groups, roles, policies, and certificates."
tags:
  - "clippings"
---
IAM identifiers - AWS Identity and Access Management

[Friendly names and paths](https://docs.aws.amazon.com/IAM/latest/UserGuide/#identifiers-friendly-names) [IAM ARNs](https://docs.aws.amazon.com/IAM/latest/UserGuide/#identifiers-arns) [Unique identifiers](https://docs.aws.amazon.com/IAM/latest/UserGuide/#identifiers-unique-ids)

IAM uses a few different identifiers for users, IAM groups, roles, policies, and server certificates. This section describes the identifiers and when you use each.

###### Topics

- [Friendly names and paths](https://docs.aws.amazon.com/IAM/latest/UserGuide/#identifiers-friendly-names)
- [IAM ARNs](https://docs.aws.amazon.com/IAM/latest/UserGuide/#identifiers-arns)
- [Unique identifiers](https://docs.aws.amazon.com/IAM/latest/UserGuide/#identifiers-unique-ids)

## Friendly names and paths

When you create a user, a role, a user group, or a policy, or when you upload a server certificate, you give it a friendly name. Examples include Bob, TestApp1, Developers, ManageCredentialsPermissions, or ProdServerCert.

If you use the IAM API or AWS Command Line Interface (AWS CLI) to create IAM resources, you can add an optional path. You can use a single path, or nest multiple paths as a folder structure. For example, you could use the nested path `/division_abc/subdivision_xyz/product_1234/engineering/` to match your company organizational structure. You could then create a policy to allow all users in that path to access the policy simulator API. To view this policy, see [IAM: Access the policy simulator API based on user path](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_examples_iam_policy-sim-path.html). For information about how a friendly name can be specified, see [the User API documentation](https://docs.aws.amazon.com/IAM/latest/APIReference/API_User.html). For additional examples of how you might use paths, see [IAM ARNs](https://docs.aws.amazon.com/IAM/latest/UserGuide/#identifiers-arns).

When you use AWS CloudFormation to create resources, you can specify a path for users, IAM groups, and roles, and customer managed policies.

If you have a user and user group in the same path, IAM doesn't automatically put the user in that user group. For example, you might create a Developers user group and specify the path as `/division_abc/subdivision_xyz/product_1234/engineering/`. If you create a user named Bob and add the same path to him, this doesn't automatically put Bob in the Developers user group. IAM doesn't enforce any boundaries between users or IAM groups based on their paths. Users with different paths can use the same resources if they've been granted permission to those resources. The number and size of IAM resources in an AWS account are limited. For more information, see [IAM and AWS STS quotas](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_iam-quotas.html).

## IAM ARNs

Most resources have a friendly name for example, a user named `Bob` or a user group named `Developers`. However, the permissions policy language requires you to specify the resource or resources using the following *Amazon Resource Name (ARN)* format.

```
arn:partition:service:region:account:resource
```

Where:

- `partition` identifies the partition for the resource. For standard AWS Regions, the partition is `aws`. If you have resources in other partitions, the partition is `` aws-`partitionname` ``. For example, the partition for resources in the China (Beijing) Region is `aws-cn`. You cannot [delegate access](https://docs.aws.amazon.com/IAM/latest/UserGuide/access_policies-cross-account-resource-access.html#access_policies-cross-account-delegating-resource-based-policies) between accounts in different partitions.
- `service` identifies the AWS product. IAM resources always use `iam`.
- `region` identifies the Region of the resource. For IAM resources, this is always kept blank.
- `account` specifies the AWS account ID with no hyphens.
- `resource` identifies the specific resource by name.

You can specify IAM and AWS STS ARNs using the following syntax. The Region portion of the ARN is blank because IAM resources are global.

Syntax:

```json
arn:aws:iam::account:root  
arn:aws:iam::account:user/user-name-with-path
arn:aws:iam::account:group/group-name-with-path
arn:aws:iam::account:role/role-name-with-path
arn:aws:iam::account:policy/policy-name-with-path
arn:aws:iam::account:instance-profile/instance-profile-name-with-path
arn:aws:sts::account:federated-user/user-name
arn:aws:sts::account:assumed-role/role-name/role-session-name
arn:aws:sts::account:self
arn:aws:iam::account:mfa/virtual-device-name-with-path
arn:aws:iam::account:u2f/u2f-token-id
arn:aws:iam::account:server-certificate/certificate-name-with-path
arn:aws:iam::account:saml-provider/provider-name
arn:aws:iam::account:oidc-provider/provider-name
arn:aws:iam::aws:contextProvider/context-provider-name
```

Many of the following examples include paths in the resource part of the ARN. Paths cannot be created or manipulated in the AWS Management Console. To use paths, you must work with the resource by using the AWS API, the AWS CLI, or the Tools for Windows PowerShell.

Examples:

```json
arn:aws:iam::123456789012:root
arn:aws:iam::123456789012:user/JohnDoe
arn:aws:iam::123456789012:user/division_abc/subdivision_xyz/JaneDoe
arn:aws:iam::123456789012:group/Developers
arn:aws:iam::123456789012:group/division_abc/subdivision_xyz/product_A/Developers
arn:aws:iam::123456789012:role/S3Access
arn:aws:iam::123456789012:role/application_abc/component_xyz/RDSAccess
arn:aws:iam::123456789012:role/aws-service-role/access-analyzer.amazonaws.com/AWSServiceRoleForAccessAnalyzer
arn:aws:iam::123456789012:role/service-role/QuickSightAction
arn:aws:iam::123456789012:policy/UsersManageOwnCredentials
arn:aws:iam::123456789012:policy/division_abc/subdivision_xyz/UsersManageOwnCredentials
arn:aws:iam::123456789012:instance-profile/Webserver
arn:aws:sts::123456789012:federated-user/JohnDoe
arn:aws:sts::123456789012:assumed-role/Accounting-Role/JaneDoe
arn:aws:sts::123456789012:self
arn:aws:iam::123456789012:mfa/JaneDoeMFA
arn:aws:iam::123456789012:u2f/user/JohnDoe/default (U2F security key)
arn:aws:iam::123456789012:server-certificate/ProdServerCert
arn:aws:iam::123456789012:server-certificate/division_abc/subdivision_xyz/ProdServerCert
arn:aws:iam::123456789012:saml-provider/ADFSProvider
arn:aws:iam::123456789012:oidc-provider/GoogleProvider
arn:aws:iam::123456789012:oidc-provider/oidc.eks.us-west-2.amazonaws.com/id/a1b2c3d4567890abcdefEXAMPLE11111
arn:aws:iam::123456789012:oidc-provider/server.example.org
arn:aws:iam::aws:contextProvider/IdentityCenter
```

The following examples provide more detail to help you understand the ARN format for different types of IAM and AWS STS resources.

- An IAM user in the account:
	###### Note
	Each IAM user name is unique. The user name is case-insensitive for the user, such as during the sign in process, but is case-sensitive when you use it in a policy or as part of an ARN.
	```json
	arn:aws:iam::123456789012:user/JohnDoe
	```
- Another user with a path reflecting an organization chart:
	```json
	arn:aws:iam::123456789012:user/division_abc/subdivision_xyz/JaneDoe
	```
- An IAM user group:
	```json
	arn:aws:iam::123456789012:group/Developers
	```
- An IAM user group with a path:
	```json
	arn:aws:iam::123456789012:group/division_abc/subdivision_xyz/product_A/Developers
	```
- An IAM role:
	```json
	arn:aws:iam::123456789012:role/S3Access
	```
- A [service-linked role](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_roles.html#iam-term-service-linked-role):
	```json
	arn:aws:iam::123456789012:role/aws-service-role/access-analyzer.amazonaws.com/AWSServiceRoleForAccessAnalyzer
	```
- A [service role](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_roles.html#iam-term-service-role):
	```json
	arn:aws:iam::123456789012:role/service-role/QuickSightAction
	```
- A managed policy:
	```json
	arn:aws:iam::123456789012:policy/ManageCredentialsPermissions
	```
- An instance profile that can be associated with an Amazon EC2 instance:
	```json
	arn:aws:iam::123456789012:instance-profile/Webserver
	```
- A federated user identified in IAM as "Paulo":
	```json
	arn:aws:sts::123456789012:federated-user/Paulo
	```
- The active session of someone assuming the role of "Accounting-Role", with a role session name of "Mary":
	```json
	arn:aws:sts::123456789012:assumed-role/Accounting-Role/Mary
	```
- Represents the caller's own session when used as a resource in an API call, such as the AWS STS API, that operates on the calling session:
	```json
	arn:aws:sts::123456789012:self
	```
- The multi-factor authentication device assigned to the user named Jorge:
	```json
	arn:aws:iam::123456789012:mfa/Jorge
	```
- A server certificate:
	```json
	arn:aws:iam::123456789012:server-certificate/ProdServerCert
	```
- A server certificate with a path that reflects an organization chart:
	```json
	arn:aws:iam::123456789012:server-certificate/division_abc/subdivision_xyz/ProdServerCert
	```
- Identity providers (SAML and OIDC):
	```json
	arn:aws:iam::123456789012:saml-provider/ADFSProvider
	arn:aws:iam::123456789012:oidc-provider/GoogleProvider
	arn:aws:iam::123456789012:oidc-provider/server.example.org
	```
- OIDC identity provider with a path that reflects an Amazon EKS OIDC identity provider URL:
	```json
	arn:aws:iam::123456789012:oidc-provider/oidc.eks.us-west-2.amazonaws.com/id/a1b2c3d4567890abcdefEXAMPLE11111
	```
- The context provider ARN used with AWS IAM Identity Center trusted identity propagation, from which the trusted context assertion was generated:
	```json
	arn:aws:iam::aws:contextProvider/IdentityCenter
	```

Another important ARN is the root user ARN. Although this is not an IAM resource, you should be familiar with the format of this ARN. It is often used in the [Principal element](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_elements_principal.html) of a resource-based policy.

- The AWS account displays the following:
	```json
	arn:aws:iam::123456789012:root
	```

The following example shows a policy you could assign to Richard to allow him to manage his access keys. Notice that the resource is the IAM user Richard.

```json
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Sid": "ManageRichardAccessKeys",
            "Effect": "Allow",
            "Action": [
                "iam:*AccessKey*",
                "iam:GetUser"
            ],
            "Resource": "arn:aws:iam::*:user/division_abc/subdivision_xyz/Richard"
        },
        {
            "Sid": "ListForConsole",
            "Effect": "Allow",
            "Action": "iam:ListUsers",
            "Resource": "*"
        }
    ]
}
```

###### Note

When you use ARNs to identify resources in an IAM policy, you can include *policy variables*. Policy variables can include placeholders for runtime information (such as the user's name) as part of the ARN. For more information, see [IAM policy elements: Variables and tags](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_variables.html)

### Using wildcards and paths in ARNs

You can use wildcards in the `resource` portion of the ARN to specify multiple users or IAM groups or policies. For example, to specify all users working on product\_1234, you use:

```json
arn:aws:iam::123456789012:user/division_abc/subdivision_xyz/product_1234/*
```

If you have users whose names start with the string `app_`, you could refer to them all with the following ARN.

```json
arn:aws:iam::123456789012:user/division_abc/subdivision_xyz/product_1234/app_*
```

To specify all users, IAM groups, or policies in your AWS account, use a wildcard after the `user/`, `group/`, or `policy/` part of the ARN, respectively.

```json
arn:aws:iam::123456789012:user/*
arn:aws:iam::123456789012:group/*
arn:aws:iam::123456789012:policy/*
```

If you specify the following ARN for a user `arn:aws:iam::111122223333:user/*` it matches both of the following examples.

```json
arn:aws:iam::111122223333:user/JohnDoe
arn:aws:iam::111122223333:user/division_abc/subdivision_xyz/JaneDoe
```

But, if you specify the following ARN for a user `arn:aws:iam::111122223333:user/division_abc*` it matches the second example, but not the first.

```json
arn:aws:iam::111122223333:user/JohnDoe
arn:aws:iam::111122223333:user/division_abc/subdivision_xyz/JaneDoe
```

Don't use a wildcard in the `user/`, `group/`, or `policy/` part of the ARN. For example, IAM does not allow the following:

```json
arn:aws:iam::123456789012:u*
```

###### Example use of paths and ARNs for a project-based user group

Paths cannot be created or manipulated in the AWS Management Console. To use paths you must work with the resource by using the AWS API, the AWS CLI, or the Tools for Windows PowerShell.

In this example, Jules in the Marketing\_Admin user group creates a project-based user group within the /marketing/ path. Jules assigns users from different parts of the company to the user group. This example illustrates that a user's path isn't related to the user groups the user is in.

The marketing group has a new product they'll be launching, so Jules creates a new user group in the /marketing/ path called Widget\_Launch. Jules then assigns the following policy to the user group, which gives the user group access to objects in the part of the `example_bucket` that is designated to this particular launch.

```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Action": "s3:*",
      "Resource": "arn:aws:s3:::example_bucket/marketing/newproductlaunch/widget/*"
    },
    {
      "Effect": "Allow",
      "Action": "s3:ListBucket*",
      "Resource": "arn:aws:s3:::example_bucket",
      "Condition": {"StringLike": {"s3:prefix": "marketing/newproductlaunch/widget/*"}}
    }
  ]
}
```

Jules then assigns the users who are working on this launch to the user group. This includes Patricia and Eli from the /marketing/ path. It also includes Chris and Chloe from the /sales/ path, and Alice and Jim from the /legal/ path.

## Unique identifiers

When IAM creates a user, user group, role, policy, instance profile, or server certificate, it assigns a unique ID to each resource. The unique ID looks like this:

`AIDAJQABLZS4A3QDU576Q`

For the most part, you use friendly names and [ARNs](https://docs.aws.amazon.com/IAM/latest/UserGuide/#identifiers-arns) when you work with IAM resources. That way you don't need to know the unique ID for a specific resource. However, the unique ID can sometimes be useful when it isn't practical to use friendly names.

One example reuses friendly names in your AWS account. Within your account, a friendly name for a user, user group, role, or policy must be unique. For example, you might create an IAM user named `John`. Your company uses Amazon S3 and has a bucket with folders for each employee. IAM user `John` is a member of an IAM user group named `User-S3-Access` with permissions that allows users access only to their own folders in the bucket. For an example of how you might create an identity-based policy that allows IAM users to access their own bucket object in S3 using the friendly name of users, see [Amazon S3: Allows IAM users access to their S3 home directory, programmatically and in the console](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_examples_s3_home-directory-console.html).

Suppose that the employee named John leaves your company and you delete the corresponding IAM user named `John`. But later another employee named John starts, and you create a new IAM user named `John`. You add the new IAM user named `John` to the existing IAM user group `User-S3-Access`. If the policy associated to the user group specifies the friendly IAM user name `John`, the policy allows the new John to access information that was left by the former John.

In general, we recommend that you specify the ARN for the resource in your policies instead of its unique ID. However, every IAM user has a unique ID, even if you create a new IAM user that reuses a friendly name you deleted before. In the example, the old IAM user `John` and the new IAM user `John` have different unique IDs. You can create resource-based policies that grant access by unique ID and not just by user name. Doing so reduces the chance that you could inadvertently grant access to information that an employee should not have.

The following example shows how you might specify unique IDs in the [Principal element](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_elements_principal.html) of a resource-based policy.

```json
"Principal": {
  "AWS": [
    "arn:aws:iam::111122223333:role/role-name",
    "AIDACKCEVSQ6C2EXAMPLE",
    "AROADBQP57FF2AEXAMPLE"
  }
```

The following example shows how you might specify unique IDs in the [Condition element](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_elements_condition.html) of a policy using global condition key [aws:userid](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_condition-keys.html#condition-keys-userid).

```
"Condition": {
    "StringLike": {
      "aws:userId": [
        "AIDACKCEVSQ6C2EXAMPLE",
        "AROADBQP57FF2AEXAMPLE:role-session-name",
        "AROA1234567890EXAMPLE:*",
        "111122223333"
      ]
    }
  }
```

Another example where user IDs can be useful is if you maintain your own database (or other store) of IAM user or role information. The unique ID can provide a unique identifier for each IAM user or role you create. This is the case when you have IAM users or roles that reuse a name, as in the previous example.

### Understanding unique ID prefixes

IAM uses the following prefixes to indicate what type of resource each unique ID applies to. Prefixes may vary based on when they were created.

| Prefix | Resource type |
| --- | --- |
| ABIA | [AWS STS service bearer token](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_credentials_bearer.html) |
| ACCA | Context-specific credential |
| AGPA | User group |
| AIDA | IAM user |
| AIPA | Amazon EC2 instance profile |
| AKIA | Access key |
| ANPA | Managed policy |
| ANVA | Version in a managed policy |
| APKA | Public key |
| AROA | Role |
| ASCA | Certificate |
| ASIA | [Temporary (AWS STS) access key IDs](https://docs.aws.amazon.com/STS/latest/APIReference/API_Credentials.html) use this prefix, but are unique only in combination with the secret access key and the session token. |

### Getting the unique identifier

The unique ID for an IAM resource is not available in the IAM console. To get the unique ID, you can use the following AWS CLI commands or IAM API calls.

AWS CLI:

IAM API:

Quicksight › developerguide

![](https://prod.us-west-2.tcx-beacon.docs.aws.dev/recommendation-beacon/similar/impressions/7f4b136c-a690-46a1-9bf6-452dd24e3df6/5MrrLMAL-XGJiyxTqqIFMGnbsgRTqkjxnpK7F7n_JkhEgJyzbNe8_g==/https:%7C%7Cdocs.aws.amazon.com%7CIAM%7Clatest%7CUserGuide%7Creference_identifiers.html/https:%7C%7Cdocs.aws.amazon.com%7Cquicksight%7Clatest%7Cdeveloperguide%7Carn-formats.html)

ARN components identify AWS resources. Key concepts: arn format, service namespace, region, account ownership, resource naming conventions, wildcard usage, s3 bucket key naming.

*May 6, 2025*

Iot-sitewise › userguide

![](https://prod.us-west-2.tcx-beacon.docs.aws.dev/recommendation-beacon/similar/impressions/7f4b136c-a690-46a1-9bf6-452dd24e3df6/5MrrLMAL-XGJiyxTqqIFMGnbsgRTqkjxnpK7F7n_JkhEgJyzbNe8_g==/https:%7C%7Cdocs.aws.amazon.com%7CIAM%7Clatest%7CUserGuide%7Creference_identifiers.html/https:%7C%7Cdocs.aws.amazon.com%7Ciot-sitewise%7Clatest%7Cuserguide%7Csecurity_iam_service-with-iam-id-based-policies.html)

AWS IoT SiteWise policy actions, resources, condition keys define permissions based on asset hierarchy, authorize time-series, asset resources, BatchPutAssetPropertyValue authorization.

*March 7, 2025*

### Discover highly rated pages

Abstracts generated by AI

IAM › UserGuide

![](https://prod.us-west-2.tcx-beacon.docs.aws.dev/recommendation-beacon/highlyRated/impressions/7f4b136c-a690-46a1-9bf6-452dd24e3df6/5MrrLMAL-XGJiyxTqqIFMGnbsgRTqkjxnpK7F7n_JkhEgJyzbNe8_g==/https:%7C%7Cdocs.aws.amazon.com%7CIAM%7Clatest%7CUserGuide%7Creference_identifiers.html/https:%7C%7Cdocs.aws.amazon.com%7CIAM%7Clatest%7CUserGuide%7Cintroduction.html)

AWS Identity Access Management controls resource access, authenticates principals, authorizes actions.

*October 22, 2024*

IAM › UserGuide

![](https://prod.us-west-2.tcx-beacon.docs.aws.dev/recommendation-beacon/highlyRated/impressions/7f4b136c-a690-46a1-9bf6-452dd24e3df6/5MrrLMAL-XGJiyxTqqIFMGnbsgRTqkjxnpK7F7n_JkhEgJyzbNe8_g==/https:%7C%7Cdocs.aws.amazon.com%7CIAM%7Clatest%7CUserGuide%7Creference_identifiers.html/https:%7C%7Cdocs.aws.amazon.com%7CIAM%7Clatest%7CUserGuide%7Cbest-practices.html)

Require temporary credentials for human users and workloads, multi-factor authentication, least-privilege permissions, and regularly review unused access.

*April 2, 2025*

[Provide feedback](https://docs.aws.amazon.com/forms/aws-doc-feedback?hidden_service_name=IAM&topic_url=https://docs.aws.amazon.com/en_us/IAM/latest/UserGuide/reference_identifiers.html)