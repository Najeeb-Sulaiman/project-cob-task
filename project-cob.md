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