---
title: "Prevent Expensive AWS API Actions with SCPs - Hacking The Cloud"
source: "https://hackingthe.cloud/aws/general-knowledge/block-expensive-actions-with-scps/"
author:
published:
created: 2025-06-06
description: "Avoid AWS bill surprises by blocking known-expensive API calls with an SCP."
tags:
  - "clippings"
---
[Skip to content](https://hackingthe.cloud/aws/general-knowledge/block-expensive-actions-with-scps/#prevent-expensive-aws-api-actions-with-scps)

Article by Nick Frichette

## Prevent Expensive AWS API Actions with SCPs

- **Original Research**
	---
- **Additional Resources**
	---
	- [Service Control Policies](https://docs.aws.amazon.com/organizations/latest/userguide/orgs_manage_policies_scps.html) (SCPs)
	- [Attaching and detaching service control policies](https://docs.aws.amazon.com/organizations/latest/userguide/orgs_manage_policies_scps_attach.html)

An ever-present danger when using AWS is accidentally making an API call that could cost you thousands of dollars. Speaking from experience, this can be a remarkably stressful time. To mitigate this risk, implementing guardrails on your account is essential. One way to do this is to block API operations which are known to be expensive. Operations like signing up for certain AWS services or creating non-deletable resources can lead to high costs.

## Understanding Service Control Policies

To help prevent billing headaches when learning about AWS security or conducting research we can use a [Service Control Policy](https://docs.aws.amazon.com/organizations/latest/userguide/orgs_manage_policies_scps.html) (SCP). An SCP is a type of organizational policy which restricts what API calls can be made by member accounts in an [AWS Organization](https://hackingthe.cloud/aws/general-knowledge/aws_organizations_defaults/). Thanks to the work of [Ian McKay](https://x.com/iann0036), and other community members, we have a list of AWS API operations which are prohibitively expensive and should be avoided.

To implement the policy below, refer to the AWS [documentation](https://docs.aws.amazon.com/organizations/latest/userguide/orgs_manage_policies_scps_attach.html) for detailed instructions on attaching and managing SCPs.

Warning

While this SCP provides a significant safeguard, it is not entirely foolproof. You can still incur high charges if not careful. This policy only blocks known problematic API calls. Always exercise caution when creating or configuring resources in AWS.