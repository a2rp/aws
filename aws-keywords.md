# AWS Keywords and Concepts

This file is a practical index of AWS service names, cloud vocabulary, and architecture concepts used throughout these notes. AWS is a cloud platform, not a programming language, so it does not have one universal set of reserved keywords. This catalog groups important terms for learning and review. It is intentionally focused on the course roadmap rather than every AWS product or API action.

For topic-wide explanations, see [README.md](README.md) and [AWS summary](aws-summary.md).

## Cloud foundations

- **Amazon Web Services (AWS)** - a cloud platform with infrastructure, managed platforms, and higher-level services.
- **Cloud computing** - on-demand access to shared computing resources over a network.
- **On-demand provisioning** - creating resources when they are needed rather than purchasing all capacity in advance.
- **Elasticity** - adding or removing capacity as demand changes.
- **Scalability** - the ability of a system to support changes in workload by changing its capacity or design.
- **Shared responsibility model** - the division of security duties between AWS and the customer.
- **Security of the cloud** - AWS responsibility for physical facilities and foundational cloud infrastructure.
- **Security in the cloud** - customer responsibility for data, identities, application code, and service configuration.
- **Infrastructure as a Service (IaaS)** - cloud resources such as virtual machines, storage, and networking that the customer configures.
- **Platform as a Service (PaaS)** - managed runtime or platform capabilities that reduce infrastructure operations.
- **Software as a Service (SaaS)** - a complete application delivered as a service.
- **Managed service** - a service where AWS operates some underlying infrastructure while the customer retains configuration and workload responsibilities.
- **Consumption model** - a pricing approach based on the selected resources and usage.
- **Service quota** - a limit on an account or resource that can constrain deployment or scaling.
- **AWS Free Tier** - account and service-specific free usage offers whose current terms must be checked before use.

## Global infrastructure

- **Region** - a geographic area containing AWS infrastructure and regional services.
- **Availability Zone (AZ)** - an isolated location within a Region used for zonal resources and multi-zone design.
- **AZ ID** - an identifier for a physical Availability Zone location that is consistent across accounts.
- **Edge location** - infrastructure used by selected services to deliver content or serve users closer to their location.
- **Local Zone** - an extension of selected AWS services closer to metropolitan areas for workloads that need lower latency.
- **Global service** - a service or control plane whose scope may span Regions.
- **Regional service** - a service or resource created and managed within a selected Region.
- **Zonal resource** - a resource whose placement is associated with one Availability Zone.
- **Data residency** - requirements about where data is stored or processed.
- **Multi-Region architecture** - a design that uses resources in more than one Region for latency, resilience, or other requirements.

## Accounts and access management

- **AWS account** - an isolation and billing boundary for AWS resources.
- **Root user** - the original account identity with broad authority; protect it and avoid routine use.
- **IAM** - AWS Identity and Access Management, which controls identities and permissions.
- **IAM Identity Center** - a service for centralized access to AWS accounts and applications.
- **Identity** - a user, group, role, or federated identity used to make requests.
- **Principal** - the identity or service making an AWS request.
- **IAM user** - a persistent identity in IAM; use cases should be assessed against federated access and temporary credentials.
- **IAM group** - a collection of IAM users for permission administration.
- **IAM role** - an identity with permissions that a trusted principal can assume.
- **Trust policy** - the role policy that specifies which principals may assume the role.
- **Permission policy** - a policy that specifies which actions are allowed or denied.
- **Identity-based policy** - a permissions policy attached to a user, group, or role.
- **Resource-based policy** - a policy attached to a resource to define which principals can access it.
- **Managed policy** - a reusable IAM policy maintained by AWS or a customer.
- **Inline policy** - a policy embedded directly into one identity.
- **Least privilege** - granting only the permissions needed for a defined task.
- **Explicit deny** - a policy decision that overrides an applicable allow.
- **Condition** - a policy clause that restricts access based on request context.
- **Permissions boundary** - a maximum permission limit for an identity.
- **Session policy** - a policy that further restricts permissions for a role session.
- **Service control policy (SCP)** - an AWS Organizations guardrail that limits the maximum permissions available to member accounts.
- **Federation** - using an external identity provider to access AWS.
- **Security Assertion Markup Language (SAML)** - a federation protocol often used for workforce sign-in.
- **OpenID Connect (OIDC)** - an identity protocol used for federation and some workload integrations.
- **Multi-factor authentication (MFA)** - an additional authentication factor used to strengthen sign-in.
- **Temporary credentials** - time-limited credentials provided for a session or role.
- **AWS Security Token Service (STS)** - a service that issues temporary security credentials.
- **Access key ID** - the public identifier associated with a programmatic credential.
- **Secret access key** - the secret component of a long-term AWS access key pair.
- **Session token** - a token used with temporary credentials.
- **Amazon Resource Name (ARN)** - a standardized identifier for an AWS resource or principal.
- **Policy evaluation** - the process that combines applicable policies, boundaries, organization controls, and request context.

### Common IAM policy fields

- **Version** - a policy language version field.
- **Statement** - one or more permission statements in a policy.
- **Effect** - whether a statement allows or denies an action.
- **Action** - the API operation or operations covered by a statement.
- **Resource** - the resource identifier or identifiers covered by a statement.
- **Principal** - the identity allowed or denied by a resource-based policy.
- **Condition** - additional requirements that must match the request.
- **Sid** - an optional statement identifier.
- **NotAction** - the set of actions excluded from an action pattern.
- **NotResource** - the set of resources excluded from a resource pattern.

## Account governance

- **AWS Organizations** - centralized management for multiple AWS accounts.
- **Management account** - the account that manages an AWS organization.
- **Member account** - an account that belongs to an AWS organization.
- **Organizational unit (OU)** - a logical group of accounts inside an organization.
- **Landing zone** - an account and governance foundation for operating workloads at scale.
- **Organization trail** - an audit trail configured to collect activity across organization accounts.
- **Tag** - a key-value label that can support ownership, automation, and cost allocation.
- **Environment separation** - separating production, development, security, and shared workloads.

## Billing and cost

- **Billing** - the account's charges for AWS resources and usage.
- **Cost allocation tag** - a tag used to group costs by owner, application, or environment.
- **AWS Budgets** - a service for tracking spend or usage against configured thresholds and notifications.
- **Cost Explorer** - a tool for exploring historical costs and usage.
- **Data transfer** - charges and network movement associated with traffic between services, Regions, or the internet.
- **On-Demand pricing** - paying for capacity without a long-term commitment.
- **Savings Plans** - commitment-based pricing options for eligible usage.
- **Reserved Instance** - a billing or capacity reservation concept available for selected services.
- **Spot Instance** - spare EC2 capacity offered with interruption risk and different pricing.
- **Idle resource** - a resource that remains provisioned while providing little or no value.
- **Total cost of ownership (TCO)** - the broader cost of running a solution, including operations and supporting services.

## Networking

- **Amazon VPC** - a logically isolated virtual network for AWS resources.
- **CIDR block** - an IP address range expressed with a network prefix.
- **IPv4** - a 32-bit Internet Protocol address format.
- **IPv6** - a 128-bit Internet Protocol address format.
- **Subnet** - an IP range within a VPC and a single Availability Zone.
- **Public subnet** - a subnet whose route table has a path to an internet gateway.
- **Private subnet** - a subnet without a direct route to an internet gateway.
- **Isolated subnet** - a subnet without a route to external networks.
- **Route table** - rules that direct network traffic by destination and target.
- **Local route** - a route that enables communication within the VPC address space.
- **Internet gateway (IGW)** - a VPC component that enables internet connectivity for eligible resources and routes.
- **NAT gateway** - a managed translation service commonly used for outbound IPv4 access from private subnets.
- **Egress-only internet gateway** - a component for outbound-only IPv6 internet access from a VPC.
- **VPC peering** - a network connection between two VPCs that use non-overlapping address ranges.
- **AWS Transit Gateway** - a hub for connecting multiple VPCs and networks.
- **VPC endpoint** - a private connection to a supported AWS service or endpoint service.
- **Gateway endpoint** - a VPC endpoint type for supported services such as Amazon S3 and DynamoDB.
- **Interface endpoint** - a VPC endpoint that uses network interfaces and AWS PrivateLink.
- **AWS PrivateLink** - private connectivity between VPCs and supported services.
- **Elastic network interface (ENI)** - a virtual network interface for a VPC resource.
- **Elastic IP address** - a static public IPv4 address allocated to an AWS account.
- **Route 53** - AWS DNS and domain-routing service.
- **Domain Name System (DNS)** - a system that maps domain names to records such as IP addresses.
- **Amazon-provided DNS resolver** - the VPC DNS resolver used by workloads in a VPC.
- **Security group** - a stateful virtual firewall associated with network interfaces or resources.
- **Network ACL (NACL)** - a stateless traffic filter associated with a subnet.
- **VPC Flow Logs** - records describing IP traffic to and from selected VPC network interfaces.
- **Ingress** - traffic entering a resource or network boundary.
- **Egress** - traffic leaving a resource or network boundary.
- **Longest prefix match** - the routing rule that prefers the most specific matching route.
- **Network address translation (NAT)** - rewriting IP address information as traffic passes through a network device.

## Compute and scaling

- **Amazon EC2** - AWS virtual server service.
- **EC2 instance** - a virtual machine running in an AWS Region and VPC.
- **Amazon Machine Image (AMI)** - a template used to launch EC2 instances.
- **Instance type** - a configuration of compute, memory, storage, and network capacity.
- **Instance lifecycle** - EC2 state changes such as pending, running, stopping, stopped, shutting down, and terminated.
- **Instance metadata** - information provided to an EC2 instance about itself and its environment.
- **Instance Metadata Service Version 2 (IMDSv2)** - a session-oriented method for accessing EC2 instance metadata.
- **Key pair** - public and private key material used for supported instance connection workflows.
- **EC2 placement** - the infrastructure placement choices available for an instance.
- **Amazon EC2 Auto Scaling** - a service for maintaining and changing EC2 fleet capacity.
- **Scaling policy** - a rule for changing capacity based on metrics or schedules.
- **Elastic Load Balancing (ELB)** - services that distribute traffic to registered targets.
- **Application Load Balancer (ALB)** - a load balancer for application-layer HTTP and HTTPS traffic.
- **Network Load Balancer (NLB)** - a load balancer for high-performance network-layer traffic.
- **Gateway Load Balancer (GWLB)** - a load balancer for deploying and scaling virtual network appliances.
- **Health check** - a test used to determine whether a target is available to receive traffic.
- **Target group** - a set of registered targets and health-check configuration for a load balancer.

## Storage

- **Amazon S3** - object storage built around buckets and objects.
- **Bucket** - a container for S3 objects.
- **Object** - stored data and associated metadata in S3.
- **Object key** - the name that identifies an object within a bucket.
- **Prefix** - a shared leading string used to group S3 object keys.
- **S3 Versioning** - retention of multiple versions of objects in a bucket.
- **S3 Lifecycle** - rules for transitioning or expiring objects.
- **S3 Block Public Access** - controls that help prevent public access to buckets and objects.
- **Bucket policy** - a resource-based policy attached to an S3 bucket.
- **Access control list (ACL)** - a legacy or specific resource access mechanism that must be evaluated against current S3 ownership and policy practices.
- **Presigned URL** - a time-limited URL that grants access to a specific S3 operation.
- **Storage class** - an S3 storage option with different access and cost characteristics.
- **Replication** - copying S3 objects to another bucket according to configured rules.
- **Multipart upload** - uploading one object as multiple parts.
- **Amazon EBS** - persistent block storage for EC2.
- **EBS volume** - a block storage device that can be attached to an EC2 instance.
- **EBS snapshot** - a point-in-time backup of an EBS volume.
- **Instance store** - temporary block storage physically associated with an instance host.
- **Amazon EFS** - managed shared file storage for supported Linux workloads.
- **Amazon FSx** - managed file systems for selected protocols and workload needs.
- **AWS Backup** - centralized backup management for supported services.

## Databases and caching

- **Amazon RDS** - managed relational database service.
- **DB engine** - relational database software used by an RDS deployment.
- **DB instance** - a database environment in RDS.
- **Multi-AZ deployment** - an RDS deployment using multiple Availability Zones for high availability or other supported capabilities.
- **Standby replica** - a replica used for failover in supported high-availability configurations.
- **Read replica** - a replica commonly used to scale read traffic.
- **Automated backup** - an RDS-managed backup process configured with a retention period.
- **DB snapshot** - a point-in-time database backup.
- **Amazon Aurora** - a relational database product compatible with selected database engines.
- **Amazon DynamoDB** - managed NoSQL key-value and document database.
- **Partition key** - a DynamoDB key attribute used to distribute data.
- **Sort key** - a DynamoDB key attribute used to order items within a partition key.
- **Primary key** - a DynamoDB key that uniquely identifies an item.
- **Global secondary index (GSI)** - an alternate DynamoDB key and query path.
- **Local secondary index (LSI)** - an alternate sort-key query path associated with a partition key.
- **Item** - a DynamoDB record composed of attributes.
- **Attribute** - a named value in a DynamoDB item.
- **Eventually consistent read** - a read that may not immediately reflect a recent write.
- **Provisioned capacity** - explicitly configured read and write capacity for selected DynamoDB tables or indexes.
- **On-demand capacity** - a DynamoDB capacity mode that adjusts with request volume according to service behavior and pricing.
- **Amazon ElastiCache** - managed in-memory caching service.
- **Cache invalidation** - removing or refreshing cached data when the source changes.
- **Time to live (TTL)** - an expiration setting for data or cache entries.

## Serverless, messaging, and workflows

- **AWS Lambda** - event-driven compute that runs code in managed execution environments.
- **Lambda function** - the code, configuration, permissions, and runtime deployed to Lambda.
- **Execution role** - an IAM role that grants a function permissions to call AWS services.
- **Event source** - a service or resource that provides events to a function.
- **Trigger** - a configured event source or invocation path that starts a function.
- **Concurrency** - the number of function invocations running at the same time.
- **Cold start** - initialization delay when a new execution environment is prepared.
- **Amazon API Gateway** - managed service for creating and operating APIs.
- **Amazon SQS** - managed message queue for decoupled components.
- **Amazon SNS** - managed notification and publish-subscribe messaging service.
- **Amazon EventBridge** - event bus and routing service for application and AWS events.
- **Amazon EventBridge Scheduler** - scheduling capability for invoking configured targets.
- **Amazon Step Functions** - workflow orchestration service.
- **Idempotency** - a property where repeating an operation does not create unintended extra effects.
- **At-least-once delivery** - a delivery model that can deliver duplicates, requiring suitable consumer behavior.
- **Dead-letter queue (DLQ)** - a queue for messages that could not be processed successfully.
- **Retry with backoff** - repeating a failed operation after increasing delays.

## Containers

- **Amazon ECS** - AWS container orchestration service.
- **Amazon EKS** - managed Kubernetes service.
- **AWS Fargate** - serverless compute for supported containers.
- **Amazon ECR** - container image registry.
- **Container image** - an immutable package used to start containers.
- **Task definition** - an ECS blueprint for running containers.
- **ECS service** - a controller that maintains and scales desired ECS tasks.
- **Kubernetes cluster** - a control plane and worker resources for running Kubernetes workloads.
- **Pod** - the smallest deployable compute unit in Kubernetes.
- **Container orchestration** - scheduling, health management, scaling, and lifecycle control for containers.

## Observability and audit

- **Amazon CloudWatch** - AWS monitoring service for metrics, logs, alarms, and dashboards.
- **Metric** - a timestamped measurement used to understand a resource or workload.
- **Log event** - a recorded application or service event.
- **Alarm** - a monitoring rule that changes state when a metric condition is met.
- **Dashboard** - a visual collection of monitoring data.
- **AWS CloudTrail** - account activity and API event recording service.
- **Management event** - an event about management operations in an AWS account.
- **Data event** - an event about data-plane activity on supported resources.
- **Event history** - a recent, searchable view of CloudTrail management events for a Region.
- **Trail** - a CloudTrail configuration that delivers events to selected destinations.
- **AWS Config** - resource configuration recording and compliance evaluation service.
- **Configuration item** - a recorded representation of a resource's configuration at a point in time.
- **AWS X-Ray** - distributed tracing service for requests across application components.

## Security and data protection

- **AWS Key Management Service (KMS)** - managed service for creating and controlling cryptographic keys.
- **Key policy** - resource policy that controls use and administration of a KMS key.
- **Envelope encryption** - encrypting data with a data key and protecting that data key with another key.
- **AWS Secrets Manager** - service for storing and managing secrets.
- **AWS Systems Manager Parameter Store** - hierarchical storage for configuration values and selected secrets.
- **AWS Security Hub** - service for aggregating security findings and posture checks.
- **Amazon GuardDuty** - threat detection service.
- **Amazon Macie** - data security and privacy service for discovering and protecting sensitive data in S3.
- **AWS WAF** - web application firewall for supported entry points.
- **AWS Shield** - managed DDoS protection service.
- **Encryption at rest** - protecting stored data using encryption.
- **Encryption in transit** - protecting data while it moves across a network.
- **Public access** - access that may be available to users outside an account or organization.
- **Cross-account access** - access granted between separate AWS accounts.
- **Incident response** - coordinated detection, containment, recovery, and learning after a security or operational event.

## Infrastructure as code and delivery

- **AWS CloudFormation** - infrastructure as code service using templates and stacks.
- **Template** - a declarative description of resources to create or manage.
- **Stack** - a CloudFormation-managed collection of resources.
- **Change set** - a preview of proposed CloudFormation changes.
- **Drift detection** - finding differences between declared infrastructure and deployed resources.
- **AWS Cloud Development Kit (CDK)** - a framework for defining cloud resources with programming languages.
- **Construct** - a reusable AWS CDK building block.
- **Synthesis** - translating CDK application code into an infrastructure template.
- **Continuous integration (CI)** - automated build and verification of changes.
- **Continuous delivery or deployment (CD)** - automated preparation or release of application changes.
- **Deployment pipeline** - stages that build, verify, and deploy software.
- **Blue-green deployment** - switching traffic between two application environments.
- **Canary deployment** - gradually releasing a change to a limited share of traffic.
- **Rollback** - restoring a previous working version after a failed change.

## Reliability and architecture

- **High availability (HA)** - design that limits service interruption during component failure.
- **Fault tolerance** - ability to continue operating despite selected failures.
- **Disaster recovery (DR)** - restoring service after a disruptive event.
- **Recovery time objective (RTO)** - target time to restore a workload.
- **Recovery point objective (RPO)** - target maximum data loss measured in time.
- **Backup and restore** - a recovery approach based on retained backups and restoration.
- **Pilot light** - a recovery pattern that keeps a minimal environment ready to scale.
- **Warm standby** - a scaled-down environment that can be increased during recovery.
- **Active-active** - a design where multiple environments serve production traffic concurrently.
- **Multi-AZ** - deploying resources across multiple Availability Zones.
- **Multi-Region** - using more than one AWS Region in a workload design.
- **AWS Well-Architected Framework** - a question-based framework for reviewing AWS workloads.
- **Operational excellence** - operating workloads, learning from events, and improving processes.
- **Security pillar** - protecting identities, systems, and data.
- **Reliability pillar** - recovering from failure and meeting availability needs.
- **Performance efficiency** - using resources effectively as demand changes.
- **Cost optimization** - managing costs while delivering business value.
- **Sustainability** - reducing unnecessary resource use and environmental impact.
- **Three-tier architecture** - presentation, application, and data layers with controlled communication.
- **Event-driven architecture** - components communicating through events and asynchronous processing.
- **Serverless architecture** - using managed services where infrastructure provisioning is abstracted from application teams.
- **Blast radius** - the scope of impact when a component, identity, or change fails.
- **Defense in depth** - applying multiple independent security controls.
- **Least privilege** - granting only required access.
- **Idempotent operation** - an operation that can be safely retried without unintended duplicate effects.
