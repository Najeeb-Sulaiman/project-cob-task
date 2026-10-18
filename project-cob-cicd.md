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

## Part B - Automate Terraform with CI/CD

This is the core of the project.

Currently, an engineer runs `terraform validate`, `terraform plan`, and `terraform apply` manually. Your job is to design and implement an automated workflow for infrastructure changes.

### Stage 1: Continuous integration - validate changes

Whenever a pull request changes Terraform code, the pipeline should automatically:

* Check out the repository.
* Initialise Terraform using the appropriate backend configuration.
* Check Terraform formatting.
* Run `terraform validate`.
* Generate a Terraform plan.
* Publish the plan in a way that reviewers can inspect it safely.

The pipeline must fail when required checks fail. An Engineer should not be able to merge a change simply because the Terraform code looks correct.

### Stage 2: Review and approval

Infrastructure changes can create resources, destroy resources, expose services, or increase cloud costs.

The CI/CD pipeline must therefore make the proposed changes visible before they are applied.

Implement a review process that allows an authorised person to inspect the plan and approve the deployment where appropriate.

**Important**: Do not automatically apply every plan generated for a pull request.

### Stage 3: Continuous delivery - apply approved changes

After a pull request is approved and merged into the designated deployment branch, the pipeline should execute the approved infrastructure change through terraform apply.

The workflow should:

* Apply only from the intended branch or deployment trigger.
* Use the correct environment and Terraform state.
* Prevent conflicting deployments against the same state.
* Stop when validation, planning, approval, or other required checks fail.
* Report whether the deployment succeeded or failed.

### Stage 4: Demonstrate the complete workflow

Demonstrate the pipeline using real changes to your data platform.

At minimum, show these scenarios:

#### Scenario A - Valid infrastructure change

Add a resource or change a configuration. Open a pull request, inspect the checks and plan, merge the approved change, and demonstrate that the pipeline applies it.

#### Scenario B - Invalid Terraform

Introduce a deliberate configuration error in a separate branch. Show that the pipeline detects the problem and prevents the deployment.

### Scenario C - Repeatability

Run the workflow again when no infrastructure changes are required. Observe the resulting plan and demonstrate that your pipeline handles an unchanged environment sensibly.

## Part C - Apply production engineering practices

Consider the controls and best practices that make infrastructure automation safe and maintainable. This is a production platform and it should be treated as such.

## Deliverables

### Submit the following:

1. **Working data engineering solution:** A data platform with Infrastructure provisioned through COB

2. **Automated Terraform pipeline:** Formatting, validation, planning, review, and controlled application of infrastructure changes.

3. **Demonstration:** Evidence of successful deployment, a failed validation, a reviewed change, and an unchanged plan.

4. **Architecture diagram:** Architectural daigram of your project implementation.

5. **Documentation:** Explain how to use your CI/CD pipeline and other implementations.

6. **Engineering decisions:** Document your engineering choices, trade-offs and lesson learned.