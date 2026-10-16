# Project COB 2

## Infrastructure Workflow Automation with CI/CD

## Business Problem

Beejan Technologies has built COB to standardise how engineering teams provision AWS infrastructure.

The Platform Engineering team has delivered the first version. Now the Data Engineering team wants to use COB to build a small, reliable data platform.

However, there is a problem: infrastructure provisioning still depends on engineers running Terraform commands manually.

An engineer must remember the right commands, execute them in the correct directory, inspect the output, and apply changes at the appropriate time. This creates room for mistakes, inconsistent deployments, and poorly reviewed infrastructure changes.

Beejan Technologies wants to improve this process.

## Part A - Become a customer of COB

Use the modules created in project 1 to provision a data platform on AWS. This could be a small data lake or any data platform solution of your choice.

### Platform-consumption requirement

Provision the infrastructure through COB's existing interfaces wherever possible.

Do not bypass COB and recreate its modules inside the consumer project simply to make the solution work.

If COB lacks a capability you genuinely need, document the gap and decide whether it belongs in the platform or should remain specific to the consuming application.
