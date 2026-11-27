# AWS Summary

A topic-wide review of Amazon Web Services (AWS). Use this file to connect cloud fundamentals, identity, networking, compute, data, application services, operations, and architecture decisions. The chapter roadmap in README.md expands these ideas into lessons, Q&A, and practical examples.

AWS changes continuously. Availability, quotas, feature names, pricing, and service behavior can vary by Region and account. Verify current details before applying a design or running a lab.

## 1. Cloud foundations

Cloud computing provides on-demand access to computing resources over a network. Instead of buying and operating all physical infrastructure, a team can provision services as needed and pay according to the selected service and usage model.

Common cloud characteristics include:

- On-demand provisioning through a console, API, CLI, or infrastructure code.
- Elastic capacity that can grow or shrink with workload needs.
- Shared infrastructure with logical isolation between customers.
- Metered usage, where charges depend on resources, requests, storage, and data transfer.
- Managed services that move some operational responsibilities to the provider.

AWS offers infrastructure services, managed platforms, and higher-level products. Choosing a managed service can reduce operational work, but it does not remove responsibility for configuration, access, data, or application behavior.

### Shared responsibility

AWS is responsible for security of the cloud, including the physical facilities, hardware, and foundational service infrastructure. The customer is responsible for security in the cloud, including identities, permissions, data, network exposure, operating systems where applicable, application code, and service configuration.

The exact division depends on the service. With a virtual machine, the customer manages more of the guest operating system and installed software. With a managed database or serverless function, AWS operates more of the underlying platform, while the customer still controls access, data, code, and configuration.

## 2. Global infrastructure

- A Region is a separate geographic area where AWS operates infrastructure and regional services.
- An Availability Zone is an isolated location within a Region. Deploying across multiple Availability Zones can reduce the impact of a single-zone failure.
- Edge locations and other edge infrastructure help deliver content or provide selected services closer to users.
- Some services and features are regional, some are global, and some are zonal. Confirm scope before assuming that a resource or setting exists everywhere.

Select Regions based on user latency, service availability, legal or residency requirements, resilience design, operational capability, and total cost. Multi-Region architecture can improve resilience or serve a distributed audience, but it adds replication, routing, operational, and cost complexity.

## 3. Accounts and identity

An AWS account is a security, resource, and billing boundary. The root user has broad account-level authority and should be protected with strong authentication and reserved for tasks that require it. Do not use the root user for routine administration.

For human access, prefer a centralized sign-in approach such as IAM Identity Center when it fits the organization. For workloads, prefer IAM roles and temporary credentials. Long-lived access keys require careful handling and should not be embedded in source code, images, scripts, or public repositories.

### IAM policy vocabulary

- A principal is an identity or service making a request.
- An action is an operation, such as reading an object or starting an instance.
- A resource is the target of the action.
- A condition adds context requirements to a permission.
- An identity-based policy is attached to an identity.
- A resource-based policy is attached to a resource.
- A role is an identity that trusted principals can assume to obtain temporary permissions.
- A permissions boundary or organization policy can restrict the maximum permissions available.

Follow least privilege: grant only the actions and resources needed, review access regularly, and use conditions where appropriate. Explicit denies and organization-level guardrails can limit access even when another policy grants it. Test policy changes carefully to avoid both accidental exposure and unintended service outages.

## 4. Management and automation interfaces

The AWS Management Console is useful for visual exploration and manual configuration. The AWS CLI and SDKs expose service APIs for repeatable commands and application integration. Infrastructure as code records resource definitions so environments can be reviewed and recreated.

Use named profiles or federated sign-in for local tools. Prefer temporary credentials and supported credential providers over manually stored keys. Never paste credentials into notes, terminal transcripts committed to Git, issue reports, or screenshots.

A sound workflow separates:

1. Authentication: identify the principal and obtain credentials.
2. Authorization: evaluate whether the principal can perform an action on a resource.
3. Request context: consider Region, endpoint, network path, and conditions.
4. Service response: inspect both successful results and structured errors.
5. Audit: record and review important administrative activity.

## 5. Organizations and governance

AWS Organizations groups accounts into an organization and can apply centralized governance. Organizational units can group accounts by purpose or environment. Service control policies establish permission guardrails for member accounts; they do not grant permissions by themselves.

Separate production, development, security, logging, and shared services when the organization needs stronger isolation or ownership boundaries. Establish consistent account contacts, Region strategy, identity management, logging, resource tagging, and baseline security controls.

A landing zone is an account and governance foundation for operating workloads at scale. Its design should be documented, automated, monitored, and reviewed rather than treated as a one-time setup.

## 6. Pricing and cost management

AWS costs can include resource time, storage capacity, API requests, data transfer, software licensing, support plans, and managed features. A service that appears idle can still incur charges through attached storage, public addresses, logs, backups, provisioned capacity, or other dependencies.

Cost management practices:

- Estimate a workload before creating resources and inspect its bill after running it.
- Use budgets and alerts to surface unusual spending early. An alert is not necessarily a spending limit.
- Tag resources consistently to support ownership and cost allocation.
- Select resource sizes and purchasing options based on actual requirements.
- Review data transfer, storage retention, request volume, and idle resources.
- Include the cost of resilience, monitoring, security, and backups in design decisions.
- Delete a lab's dependent resources and verify cleanup in the relevant services.

Pricing and free usage programs change. Check current terms for the account and Region instead of assuming a service is free.

## 7. Networking

A VPC is a logically isolated virtual network. Its CIDR ranges define address space. Subnets divide that address space and belong to one Availability Zone. A subnet is public when its route table provides a path to an internet gateway; a public IP address and applicable security rules are also needed for direct internet connectivity.

Important components:

- Route tables direct traffic based on destination and target.
- An internet gateway provides a route between a VPC and the internet for eligible resources.
- A NAT gateway commonly allows private-subnet resources to initiate outbound IPv4 connections without accepting unsolicited inbound connections.
- VPC endpoints provide supported private paths to AWS services.
- Security groups are stateful controls associated with network interfaces or resources.
- Network ACLs are stateless subnet-level controls.
- Route 53 provides DNS and routing capabilities.
- VPC Flow Logs record information about network traffic to and from selected network interfaces, subnets, or VPCs.

Plan non-overlapping CIDR ranges before connecting VPCs or on-premises networks. Start with narrow, deliberate routes and security rules. Use private subnets for resources that should not be directly reachable from the internet. Network reachability requires checking routes, gateways, address assignment, DNS, security groups, network ACLs, and service-level permissions together.

## 8. Compute

### Amazon EC2

An EC2 instance is a virtual server. An Amazon Machine Image provides a launch template for the operating system and other software. Instance types vary in compute, memory, storage, and networking characteristics.

The instance lifecycle matters:

- Stopping an EBS-backed instance keeps its attached EBS data, though other charges may remain.
- Terminating an instance removes the virtual server and may also delete some attached resources depending on settings.
- Instance store is temporary storage whose data is not durable across relevant lifecycle events.
- An EBS volume is persistent block storage that can be attached to supported instances.
- An EBS snapshot provides a point-in-time backup mechanism for a volume.

Use instance roles for AWS access from EC2 instead of placing long-lived keys on a server. Apply security updates, restrict inbound access, log administrative activity, and automate replacement where practical.

### Scaling and load balancing

Elastic Load Balancing distributes incoming traffic across healthy targets. Target groups define where requests go and how target health is checked. EC2 Auto Scaling changes instance capacity based on configured policies and health signals.

Scaling should consider application startup time, health checks, capacity limits, database connection counts, and downstream bottlenecks. A load balancer and Auto Scaling do not make an application stateless by themselves.

## 9. Storage

### Amazon S3

S3 is object storage. A bucket holds objects; an object has a key and data, and keys can be organized using prefixes. S3 is not a traditional mounted block disk.

Common controls and features:

- Block Public Access helps prevent unintended public access.
- Bucket policies and IAM policies control authorization.
- Versioning can retain multiple object versions and help recover from overwrites or deletes.
- Lifecycle rules transition or expire objects according to configured policies.
- Encryption protects stored data, with key-management choices based on requirements.
- Replication can copy objects between buckets or Regions when configured.
- Presigned URLs provide time-limited access to a specific operation or object.

Keep data private by default. Enable public access only for a deliberate, reviewed use case. Consider retention, versioning, lifecycle cost, replication, and recovery requirements together.

### Shared file systems

Amazon EFS provides managed shared file storage for supported Linux workloads. Amazon FSx offers managed file systems for specific workload and protocol requirements. Select storage by access pattern, consistency, performance, sharing model, availability, durability, and cost rather than by service name alone.

## 10. Databases and caching

Amazon RDS operates supported relational database engines as a managed service. The customer still chooses schema, queries, network access, authentication, backup retention, and operational configuration.

Do not confuse availability with read scaling:

- A Multi-AZ standby is primarily for failover and high availability; whether it serves reads depends on the specific deployment type.
- A read replica is primarily for scaling read traffic and may have replication delay.
- Backups and snapshots support recovery but need retention and restore planning.
- Applications must reconnect and handle transient failures during failover.

DynamoDB is a managed NoSQL database suited to key-value and document access patterns. Design keys and indexes around the queries the application must perform. Avoid treating it as a relational database with arbitrary joins.

ElastiCache provides managed caching options. A cache can reduce latency and database load, but it introduces expiration, invalidation, stale data, and failure behavior that the application must handle.

## 11. Content delivery and API entry points

Route 53 can host DNS records and support routing policies. DNS records map names to endpoints, but DNS caching and propagation affect how quickly changes are observed.

CloudFront is a content delivery network that can cache content at edge locations and connect to configured origins. Cache behavior, origin access, TLS, invalidation, and sensitive response handling should be designed together.

API Gateway can expose managed API endpoints and integrate with backend services. Consider authentication, authorization, throttling, request validation, payload limits, observability, and deployment stages.

## 12. Serverless and event-driven applications

AWS Lambda runs functions in response to configured events. The service manages the underlying compute fleet, while developers manage function code, permissions, configuration, and operational behavior.

Design functions to be:

- Focused on a clear unit of work.
- Idempotent when retries are possible.
- Observable through structured logs and metrics.
- Protected by an execution role with narrow permissions.
- Designed for timeouts, concurrency, payload size, and downstream limits.
- Safe when events are duplicated, delayed, or delivered out of order.

SQS is a queue for decoupling producers and consumers. SNS distributes notifications to subscribers. EventBridge routes events based on configured rules. Step Functions coordinates multi-step workflows, including retries and error handling.

Choose messaging based on delivery semantics, ordering, retention, fan-out, filtering, replay needs, and operational ownership. Do not assume that asynchronous delivery happens exactly once.

## 13. Containers

Amazon ECS runs containerized applications using AWS-managed orchestration. AWS Fargate provides serverless compute for supported container workloads. Amazon EKS offers managed Kubernetes control-plane capabilities.

Choose a container platform based on team expertise, portability requirements, operational burden, scaling, networking, security, and cost. A container still needs image security, secrets management, health checks, logs, resource limits, and a deployment strategy.

## 14. Monitoring, audit, and configuration

Amazon CloudWatch collects metrics, logs, and alarms for AWS resources and applications. A metric is a measurement over time; logs capture event details; traces can connect activity across components. Alarms can notify or trigger actions, but useful alerts need thresholds and ownership.

AWS CloudTrail records account activity from the Console, CLI, SDKs, and service APIs. Event history provides a limited recent view of management events; longer retention or broader event coverage requires configured trails or event data stores.

AWS Config can record resource configuration and evaluate resources against rules. It complements CloudTrail: CloudTrail answers what API activity occurred, while Config helps show resource configuration state and changes.

Define what to monitor before production: availability, latency, errors, saturation, business outcomes, security events, and cost signals. Monitor the monitoring path itself.

## 15. Security and data protection

Build security into identity, network, application, and data design:

- Protect root credentials and require strong authentication for privileged identities.
- Prefer federated human access and short-lived workload credentials.
- Apply least privilege and review public or cross-account access.
- Encrypt sensitive data in transit and at rest where appropriate.
- Use AWS KMS to manage encryption keys and key policies.
- Use Secrets Manager or Parameter Store for application configuration and secrets according to the need.
- Rotate credentials where supported and remove unused secrets.
- Keep audit logs, restrict access to them, and plan incident response.
- Patch operating systems, dependencies, and container images.
- Use private network paths where they reduce exposure, while still enforcing identity permissions.

Encryption does not replace access control, backups, retention rules, or careful key administration.

## 16. Infrastructure as code and delivery

CloudFormation describes AWS resources in templates and manages them as stacks. AWS CDK lets developers define infrastructure using supported programming languages and synthesizes templates for deployment.

Infrastructure code improves reviewability and repeatability, but it can also create or delete real resources. Review planned changes, protect stateful resources, separate environments, and restrict deployment permissions.

A delivery pipeline typically includes source control, build, test, artifact storage, deployment, and approval or rollout controls. Safe releases use health checks, staged rollout, rollback plans, and clear ownership. Keep application secrets out of build logs and source files.

## 17. Reliability and recovery

Design for failures rather than assuming components never fail. Use health checks, bounded retries with backoff, timeouts, idempotency, queues, redundancy, and tested recovery procedures.

Recovery concepts:

- High availability reduces interruption during component failure.
- Backup supports restoring lost or corrupted data.
- Disaster recovery restores a workload after a larger disruption.
- RTO is the target time to restore service.
- RPO is the target amount of data loss measured in time.
- Multi-AZ design handles some zonal failures; multi-Region design addresses a wider set of failures but adds complexity.

A backup is not proven until it has been restored successfully. Regularly test recovery steps and document dependencies, owners, and decision points.

## 18. Well-Architected review

Use the AWS Well-Architected Framework as a set of questions for improving a workload. Its six pillars are:

1. Operational excellence - run, monitor, learn, and improve.
2. Security - protect identities, systems, and data.
3. Reliability - recover from failures and meet availability requirements.
4. Performance efficiency - use resources effectively as demand and technology change.
5. Cost optimization - deliver business value while managing spending.
6. Sustainability - reduce unnecessary resource use and environmental impact.

A review is a design conversation. Record risks, priorities, remediation owners, and follow-up dates. Framework alignment does not guarantee that an application is secure, compliant, or available.

## 19. Common architecture patterns

### Three-tier application

A typical pattern places a public load balancer in public subnets, application compute in private subnets, and a managed database in isolated private subnets. Security groups permit only necessary paths. Multi-AZ deployment, backups, logs, and scaling policies depend on the workload's requirements.

### Serverless event workflow

A request can enter through API Gateway, invoke Lambda, validate identity and input, read or write data, and publish an event or queue message. EventBridge or SQS can decouple later processing. CloudWatch provides operational signals and CloudTrail records API activity.

### Static content delivery

S3 can store static objects while CloudFront serves cached content. Keep the bucket private and configure an origin access mechanism. Add DNS, TLS, cache policies, logging, and deployment invalidation as needed.

Patterns are starting points, not universal blueprints. Validate each one against data sensitivity, failure tolerance, expected traffic, team skills, and cost.

## 20. Troubleshooting checklist

When a request fails, trace it from the caller to the service:

1. Confirm the active account, principal, Region, and endpoint.
2. Check authentication and temporary credential expiration.
3. Read the exact authorization error and inspect identity, resource, and organization policies.
4. Verify DNS, CIDR ranges, route-table targets, gateways, and VPC endpoint policies.
5. Check security groups, network ACLs, host firewalls, and service-level controls.
6. Confirm resource state, health checks, quotas, payload limits, and service availability.
7. Review application logs, CloudWatch metrics, and relevant CloudTrail events.
8. Check whether data, storage, or dependent resources were removed or changed.
9. Consider eventual consistency, retries, timeouts, and duplicate events.
10. Record the root cause and add a monitoring or prevention action.

## Review reminders

- Availability depends on architecture and configuration, not only on the service name.
- Managed services still require secure configuration and operational ownership.
- A public subnet does not automatically mean every resource in it is reachable from the internet.
- An allow rule in one security layer does not override a deny or missing route in another.
- Backups, replicas, and caches solve different problems.
- Cost optimization must preserve required security, reliability, and performance.
- Verify Region, account, cost, and cleanup before running hands-on work.
