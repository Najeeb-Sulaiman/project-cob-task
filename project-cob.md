# Project COB

## Internal Infrastructure Provisioning Platform

### Project Brief

**Team:** Platform Engineering  
**Company:** Beejan Technologies  
**Project:** COB  
**Objective:** Standardise and accelerate AWS infrastructure provisioning across the engineering organisation.

---

## Background

Beejan Technologies has grown rapidly. The engineering organisation now consists of several application, data and analytics teams, all running workloads on AWS.

As the number of teams has increased, the Platform Engineering team has become a bottleneck.

When a team needs infrastructure, they currently submit a request to Platform Engineering. An engineer then manually provisions the required AWS resources through the AWS Console or writes Terraform specifically for that project.

A typical request might require:

- A VPC and subnets
- Security groups
- IAM roles and policies
- S3 storage
- EC2 instances
- ECS infrastructure
- RDS databases
- Other supporting resources

Although this approach worked when the company was smaller, it is becoming increasingly difficult to manage.

Different teams are now using different configurations for similar resources. Some S3 buckets have versioning enabled while others do not. IAM policies are inconsistent. Naming and tagging conventions vary. Network configurations differ between projects, and infrastructure changes are difficult to track.

The Platform Engineering team has been asked to solve this problem.

---

# The Problem

Beejan Technologies needs a **standardised way for engineers to provision AWS infrastructure without repeatedly designing and implementing the same infrastructure from scratch.**

The platform should:

- Reduce the time required to provision infrastructure.
- Standardise common AWS configurations.
- Encourage secure-by-default infrastructure.
- Reduce configuration inconsistencies.
- Make infrastructure reusable across projects and environments.
- Allow Platform Engineering to improve standards centrally without rewriting every application.

The team has decided to build an internal Terraform-based platform called **COB**.

---

# Your Assignment

You are a Platform Engineer on the COB team.

Your responsibility is to design and implement the first version of COB as a **reusable internal infrastructure provisioning platform**.

COB should provide reusable Terraform modules that other engineering teams can consume to provision standardised AWS infrastructure.

The platform should not simply be a collection of Terraform files for individual AWS resources.

You are expected to identify meaningful infrastructure capabilities and design reusable abstractions around them.

---

# Platform Capabilities

The first version of COB must provide reusable capabilities for:

### Networking

A standard AWS network foundation that can be used by engineering workloads.

It should support the required VPC components, subnets, routing and security boundaries.

### Identity and Access

Reusable patterns for creating IAM resources while encouraging least-privilege access.

### Object Storage

A standardised S3 storage capability with appropriate security and operational defaults.

Consider requirements such as encryption, versioning, lifecycle management, naming and tagging.

### Compute

Reusable infrastructure for workloads that need:

- EC2
- ECS

The platform should make sensible networking and IAM configurations available to workloads without requiring every team to implement them independently.

### Relational Database

A reusable RDS capability for teams that require a managed relational database.

The module should account for networking, security and operational considerations.

### Data Platform Services

Reusable capabilities for teams that need to expose data stored in S3 to analytics users.

This should include appropriate integration with:

- AWS Glue Data Catalog
- Amazon Athena

---

# Designing the Abstractions

One of the most important requirements of COB is that the modules must provide **real abstractions**.

Do not simply create modules that hide a single AWS resource.

For example, a module whose only purpose is to expose:

```text
aws_s3_bucket
```

behind another interface does not provide much value.

Instead, think about what an engineering team actually needs.

A standardised object-storage capability might include several related resources and configurations required to make storage secure, observable and operationally consistent.

The same principle should be applied throughout the platform.

Your module boundaries are part of the design challenge.

---

# Platform Consumers

COB will eventually be used by several teams.

For example:

```text
Application Engineering
        │
        ├── Web applications
        │
        └── Microservices

Data Engineering
        │
        ├── Data ingestion
        ├── Data processing
        └── Analytics

Analytics Engineering
        │
        └── Data consumption
```

Each team should be able to consume COB without needing to understand every implementation detail behind the platform.

The platform should expose a clean interface through Terraform variables and outputs.

---

# Environments

COB must support multiple environments.

At minimum:

```text
dev
prod
```

The same platform capabilities should be reusable across environments while allowing appropriate configuration differences.

Avoid duplicating infrastructure code simply because the environment changes.

---

# Engineering Standards

COB is intended to become an internal company standard, so the platform should establish sensible defaults.

Consider how COB can enforce or encourage:

- Consistent naming
- Standard resource tagging
- Encryption at rest
- Secure S3 configuration
- Least-privilege IAM
- Appropriate network isolation
- Secure security-group rules
- Resource lifecycle management
- Environment separation
- Cost-conscious infrastructure

These standards should be implemented through the platform wherever practical rather than relying entirely on individual developers to remember them.

---

# Expected Repository

The exact structure is your decision, but the repository should clearly separate:

```text
Platform modules
Environment configuration
Documentation
Examples / consumers
```

A new engineer joining the Platform Engineering team should be able to understand the repository without requiring a walkthrough from you.

---

# Platform Demonstration

COB itself is the product you are building.

Your demonstration should therefore show how an engineering team would consume it.

Create at least one example consumer that uses COB to provision a realistic combination of AWS infrastructure.

For example, an engineering team should be able to compose several COB capabilities rather than manually recreating the underlying AWS resources.

The example consumer is intended to prove that your abstractions are genuinely reusable.

---

# Documentation

Your platform must include documentation for engineers who will consume it.

Document:

- What COB is
- The problem it solves
- Available capabilities
- How modules are consumed
- Required inputs
- Outputs
- Supported environments
- Security considerations
- Important assumptions
- Known limitations

Also document the major architectural decisions you made and the reasoning behind them.

---

# Architecture

Provide an architecture diagram showing the major components of COB and the AWS infrastructure it provisions.

The diagram should make the relationships between networking, IAM, compute, storage and managed services clear.

Do not simply produce a diagram containing every AWS icon.

The diagram should communicate the architecture to another engineer.

---

# Definition of Done

COB is considered complete when:

- The core platform capabilities can be provisioned through Terraform.
- Modules are reusable across multiple projects and environments.
- Modules provide meaningful abstractions rather than thin wrappers.
- Infrastructure follows consistent security and configuration standards.
- The platform can provision a realistic example environment.
- The Terraform code is maintainable and clearly organised.
- Engineers can understand how to consume the platform from the documentation.
- Major architectural and security decisions can be explained and defended.

---

# Final Outcome

At the end of this project, Beejan Technologies should have the foundation of an internal infrastructure platform that allows engineering teams to move from:

> **"We need AWS infrastructure. Can Platform Engineering create it for us?"**

to:

> **"We can provision the infrastructure we need using the company's standard platform."**

Your goal is not to provision as many AWS resources as possible.

Your goal is to demonstrate that you can **design reusable infrastructure abstractions, encode engineering standards in Terraform, and build a platform that other engineers can confidently use.**

The next project will treat COB as a real internal platform and use it to build a production-style data engineering solution.
