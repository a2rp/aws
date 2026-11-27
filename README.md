# AWS: Practical Learning Notes

These personal learning notes provide a structured path for understanding Amazon Web Services (AWS), from cloud foundations to designing, securing, operating, and reviewing real workloads.

AWS is a broad and continuously evolving platform. This course focuses on durable concepts and commonly used services. Service availability, limits, names, pricing, and console workflows can vary by Region and can change over time. Each future chapter should state important version or availability details where they affect the guidance.

## Learning outcomes

By following the roadmap, you will learn to:

- Explain cloud computing, the AWS shared responsibility model, and the difference between Regions, Availability Zones, and edge locations.
- Secure an AWS account with strong sign-in practices, IAM roles, temporary credentials, and least-privilege permissions.
- Use the AWS Management Console, AWS CLI, and SDKs without exposing credentials.
- Design VPC networks with deliberate address ranges, public and private subnets, route tables, gateways, endpoints, and security controls.
- Select and operate compute, storage, database, networking, and application-integration services for a workload.
- Build event-driven and serverless systems, as well as container-based applications.
- Monitor service health, audit account activity, protect data, and respond to operational problems.
- Automate infrastructure and delivery, plan for failure, and review architectures for security, reliability, performance, cost, and sustainability.

## Prerequisites

You should be comfortable using a computer, navigating files, and reading basic application logs. Familiarity with HTTP, IP addresses, DNS, Linux or Windows, and a programming language will help, but the roadmap introduces cloud-specific networking and service concepts as needed.

An AWS account is optional for reading the notes. Hands-on work may create billable resources. Before using an account, secure the root user, enable multi-factor authentication, create an appropriate administrative sign-in, configure billing alerts or budgets, and use temporary credentials where possible. Check current prices and service limits before starting a lab. Remove resources after a lab and verify that dependent resources, such as disks, snapshots, public IP addresses, load balancers, and logs, are also handled. Never commit passwords, access keys, session tokens, private keys, or account-specific secrets to this repository.

## Quick guides

- [AWS summary](aws-summary.md)
- [AWS keywords and concepts](aws-keywords.md)

## How to use these notes

1. Read the roadmap in order. The early chapters establish account security and networking before introducing services that depend on them.
2. Keep the summary nearby for a topic-wide review and use the keywords file as a quick index.
3. For each chapter, use its lesson to learn the concepts, its Q&A to review decisions and edge cases, and its example to practice a coherent task.
4. Treat every lab as a small, cost-aware exercise. Identify the resources it creates, the Region in use, and the cleanup steps before running it.
5. Recheck time-sensitive service behavior, quotas, and pricing against current AWS information when you later work through the detailed chapters.

## Account and cost safety

Cloud resources can continue to incur charges while they exist, even when an application is idle. A stopped virtual machine does not automatically remove separately billed storage or related resources. Serverless services can also incur charges through requests, data transfer, logs, or supporting resources.

Use a dedicated learning account when practical. Protect root access, use a named administrative identity through IAM Identity Center where available, and grant workloads temporary role credentials. Start with the smallest resources needed for a lab. Set spending notifications before creating resources, but do not treat a budget notification as a hard spending cap. Check billing data after each exercise and confirm cleanup in the relevant service consoles or CLI.

## Course roadmap

| No. | Lesson | Q&A | Example |
|---:|---|---|---|
| 001 | [Cloud computing, AWS, and the shared responsibility model](lessons/001-cloud-computing-aws-and-shared-responsibility.md) | [Open Q&A](qnas/001-cloud-computing-aws-and-shared-responsibility.md) | [Open example](examples/001-cloud-computing-aws-and-shared-responsibility.md) |
| 002 | [AWS global infrastructure: Regions, Availability Zones, and edge locations](lessons/002-aws-global-infrastructure-regions-availability-zones-and-edge-locations.md) | [Open Q&A](qnas/002-aws-global-infrastructure-regions-availability-zones-and-edge-locations.md) | [Open example](examples/002-aws-global-infrastructure-regions-availability-zones-and-edge-locations.md) |
| 003 | [AWS accounts, root user, and secure sign-in](lessons/003-aws-accounts-root-user-and-secure-sign-in.md) | [Open Q&A](qnas/003-aws-accounts-root-user-and-secure-sign-in.md) | [Open example](examples/003-aws-accounts-root-user-and-secure-sign-in.md) |
| 004 | [IAM identities, policies, roles, and least privilege](lessons/004-iam-identities-policies-roles-and-least-privilege.md) | [Open Q&A](qnas/004-iam-identities-policies-roles-and-least-privilege.md) | [Open example](examples/004-iam-identities-policies-roles-and-least-privilege.md) |
| 005 | [AWS Console, CLI, SDKs, and credential profiles](lessons/005-aws-console-cli-sdks-and-credential-profiles.md) | [Open Q&A](qnas/005-aws-console-cli-sdks-and-credential-profiles.md) | [Open example](examples/005-aws-console-cli-sdks-and-credential-profiles.md) |
| 006 | [AWS Organizations, accounts, and governance guardrails](lessons/006-aws-organizations-accounts-and-governance-guardrails.md) | [Open Q&A](qnas/006-aws-organizations-accounts-and-governance-guardrails.md) | [Open example](examples/006-aws-organizations-accounts-and-governance-guardrails.md) |
| 007 | [AWS pricing, billing, budgets, and cost awareness](lessons/007-aws-pricing-billing-budgets-and-cost-awareness.md) | [Open Q&A](qnas/007-aws-pricing-billing-budgets-and-cost-awareness.md) | [Open example](examples/007-aws-pricing-billing-budgets-and-cost-awareness.md) |
| 008 | [VPC foundations, CIDR ranges, and subnet design](lessons/008-vpc-foundations-cidr-ranges-and-subnet-design.md) | [Open Q&A](qnas/008-vpc-foundations-cidr-ranges-and-subnet-design.md) | [Open example](examples/008-vpc-foundations-cidr-ranges-and-subnet-design.md) |
| 009 | [VPC routing, internet gateways, NAT, and endpoints](lessons/009-vpc-routing-internet-gateways-nat-and-endpoints.md) | [Open Q&A](qnas/009-vpc-routing-internet-gateways-nat-and-endpoints.md) | [Open example](examples/009-vpc-routing-internet-gateways-nat-and-endpoints.md) |
| 010 | [Network security groups, network ACLs, DNS, and flow logs](lessons/010-network-security-groups-network-acls-dns-and-flow-logs.md) | [Open Q&A](qnas/010-network-security-groups-network-acls-dns-and-flow-logs.md) | [Open example](examples/010-network-security-groups-network-acls-dns-and-flow-logs.md) |
| 011 | [Amazon EC2 instances, AMIs, instance types, and lifecycle](lessons/011-amazon-ec2-instances-amis-instance-types-and-lifecycle.md) | [Open Q&A](qnas/011-amazon-ec2-instances-amis-instance-types-and-lifecycle.md) | [Open example](examples/011-amazon-ec2-instances-amis-instance-types-and-lifecycle.md) |
| 012 | [EC2 storage, EBS volumes, snapshots, and instance store](lessons/012-ec2-storage-ebs-volumes-snapshots-and-instance-store.md) | [Open Q&A](qnas/012-ec2-storage-ebs-volumes-snapshots-and-instance-store.md) | [Open example](examples/012-ec2-storage-ebs-volumes-snapshots-and-instance-store.md) |
| 013 | [Load balancing, target groups, and EC2 Auto Scaling](lessons/013-load-balancing-target-groups-and-ec2-auto-scaling.md) | [Open Q&A](qnas/013-load-balancing-target-groups-and-ec2-auto-scaling.md) | [Open example](examples/013-load-balancing-target-groups-and-ec2-auto-scaling.md) |
| 014 | [Amazon S3 buckets, objects, security, and lifecycle](lessons/014-amazon-s3-buckets-objects-security-and-lifecycle.md) | [Open Q&A](qnas/014-amazon-s3-buckets-objects-security-and-lifecycle.md) | [Open example](examples/014-amazon-s3-buckets-objects-security-and-lifecycle.md) |
| 015 | [Shared file systems and storage selection: EFS and FSx](lessons/015-shared-file-systems-and-storage-selection-efs-and-fsx.md) | [Open Q&A](qnas/015-shared-file-systems-and-storage-selection-efs-and-fsx.md) | [Open example](examples/015-shared-file-systems-and-storage-selection-efs-and-fsx.md) |
| 016 | [Route 53, DNS routing, and CloudFront content delivery](lessons/016-route-53-dns-routing-and-cloudfront-content-delivery.md) | [Open Q&A](qnas/016-route-53-dns-routing-and-cloudfront-content-delivery.md) | [Open example](examples/016-route-53-dns-routing-and-cloudfront-content-delivery.md) |
| 017 | [Amazon RDS, relational databases, and high availability](lessons/017-amazon-rds-relational-databases-and-high-availability.md) | [Open Q&A](qnas/017-amazon-rds-relational-databases-and-high-availability.md) | [Open example](examples/017-amazon-rds-relational-databases-and-high-availability.md) |
| 018 | [Amazon DynamoDB, key-value data, and access patterns](lessons/018-amazon-dynamodb-key-value-data-and-access-patterns.md) | [Open Q&A](qnas/018-amazon-dynamodb-key-value-data-and-access-patterns.md) | [Open example](examples/018-amazon-dynamodb-key-value-data-and-access-patterns.md) |
| 019 | [Caching and Amazon ElastiCache](lessons/019-caching-and-amazon-elasticache.md) | [Open Q&A](qnas/019-caching-and-amazon-elasticache.md) | [Open example](examples/019-caching-and-amazon-elasticache.md) |
| 020 | [AWS Lambda and serverless compute](lessons/020-aws-lambda-and-serverless-compute.md) | [Open Q&A](qnas/020-aws-lambda-and-serverless-compute.md) | [Open example](examples/020-aws-lambda-and-serverless-compute.md) |
| 021 | [API Gateway, event sources, and serverless APIs](lessons/021-api-gateway-event-sources-and-serverless-apis.md) | [Open Q&A](qnas/021-api-gateway-event-sources-and-serverless-apis.md) | [Open example](examples/021-api-gateway-event-sources-and-serverless-apis.md) |
| 022 | [Queues, notifications, and event routing with SQS, SNS, and EventBridge](lessons/022-queues-notifications-and-event-routing-with-sqs-sns-and-eventbridge.md) | [Open Q&A](qnas/022-queues-notifications-and-event-routing-with-sqs-sns-and-eventbridge.md) | [Open example](examples/022-queues-notifications-and-event-routing-with-sqs-sns-and-eventbridge.md) |
| 023 | [AWS Step Functions and durable workflow orchestration](lessons/023-aws-step-functions-and-durable-workflow-orchestration.md) | [Open Q&A](qnas/023-aws-step-functions-and-durable-workflow-orchestration.md) | [Open example](examples/023-aws-step-functions-and-durable-workflow-orchestration.md) |
| 024 | [Containers on AWS: ECS, Fargate, and EKS](lessons/024-containers-on-aws-ecs-fargate-and-eks.md) | [Open Q&A](qnas/024-containers-on-aws-ecs-fargate-and-eks.md) | [Open example](examples/024-containers-on-aws-ecs-fargate-and-eks.md) |
| 025 | [CloudWatch metrics, logs, alarms, and operational dashboards](lessons/025-cloudwatch-metrics-logs-alarms-and-operational-dashboards.md) | [Open Q&A](qnas/025-cloudwatch-metrics-logs-alarms-and-operational-dashboards.md) | [Open example](examples/025-cloudwatch-metrics-logs-alarms-and-operational-dashboards.md) |
| 026 | [CloudTrail, AWS Config, and account auditing](lessons/026-cloudtrail-aws-config-and-account-auditing.md) | [Open Q&A](qnas/026-cloudtrail-aws-config-and-account-auditing.md) | [Open example](examples/026-cloudtrail-aws-config-and-account-auditing.md) |
| 027 | [Encryption, AWS KMS, Secrets Manager, and Parameter Store](lessons/027-encryption-aws-kms-secrets-manager-and-parameter-store.md) | [Open Q&A](qnas/027-encryption-aws-kms-secrets-manager-and-parameter-store.md) | [Open example](examples/027-encryption-aws-kms-secrets-manager-and-parameter-store.md) |
| 028 | [Infrastructure as code with CloudFormation and AWS CDK](lessons/028-infrastructure-as-code-with-cloudformation-and-aws-cdk.md) | [Open Q&A](qnas/028-infrastructure-as-code-with-cloudformation-and-aws-cdk.md) | [Open example](examples/028-infrastructure-as-code-with-cloudformation-and-aws-cdk.md) |
| 029 | [Application delivery, deployment pipelines, and safe releases](lessons/029-application-delivery-deployment-pipelines-and-safe-releases.md) | [Open Q&A](qnas/029-application-delivery-deployment-pipelines-and-safe-releases.md) | [Open example](examples/029-application-delivery-deployment-pipelines-and-safe-releases.md) |
| 030 | [Backups, disaster recovery, and multi-Region design](lessons/030-backups-disaster-recovery-and-multi-region-design.md) | [Open Q&A](qnas/030-backups-disaster-recovery-and-multi-region-design.md) | [Open example](examples/030-backups-disaster-recovery-and-multi-region-design.md) |
| 031 | [AWS security practices and the Well-Architected Framework](lessons/031-aws-security-practices-and-the-well-architected-framework.md) | [Open Q&A](qnas/031-aws-security-practices-and-the-well-architected-framework.md) | [Open example](examples/031-aws-security-practices-and-the-well-architected-framework.md) |
| 032 | [Capstone: design and review a production-ready AWS workload](lessons/032-capstone-design-and-review-a-production-ready-aws-workload.md) | [Open Q&A](qnas/032-capstone-design-and-review-a-production-ready-aws-workload.md) | [Open example](examples/032-capstone-design-and-review-a-production-ready-aws-workload.md) |

## Repository structure

- README.md - course introduction, setup guidance, and linked roadmap.
- LICENSE - MIT license for this notes repository.
- aws-summary.md - topic-wide AWS review and architecture concepts.
- aws-keywords.md - AWS service names, cloud vocabulary, and related concepts.
- lessons/ - chapter explanations, to be written in future steps.
- qnas/ - chapter questions and answers, to be written in future steps.
- examples/ - hands-on chapter examples, to be written in future steps.

## Future chapter content

The lesson, Q&A, and example files are intentionally empty in this initial scaffold. Their detailed content will be written in future steps, one chapter at a time.

## License

This repository is licensed under the MIT License. See [LICENSE](LICENSE).
