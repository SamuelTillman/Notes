# Terraform Associate (004) Study Plan

A self-paced study plan organized by the official exam objectives. There is no fixed day count. Work each objective in order, check off every concept and task as you genuinely master it, and only move to the next objective once the readiness gate at the end of the section is true. Mirror this with hands-on practice: type the commands, do not just read them.

## Exam Facts

These are taken from HashiCorp's certification page. Verify them against the official page before you book, since HashiCorp updates exam details over time.

- Format: the certification page lists multiple choice. The official sample questions page shows three question styles in practice: true or false, multiple choice with one correct answer, and multiple answer where the question states how many to pick
- Duration: 1 hour
- Delivery: online proctored
- Cost: 70.50 USD plus locally applicable taxes and fees
- Free retake: not included
- Credential validity: 2 years
- Prerequisites: basic terminal skills, and an understanding of on-premises and cloud architecture
- Language: English

Honesty note: HashiCorp does not publish an official question count, a numeric passing score, or per-objective percentage weights for the 004 exam, and the result is reported as pass or fail. The official sample questions page provides five example questions and states that the questions are not meant to trick you and test knowledge of Terraform rather than obscure details. Do not trust any source that states an exact passing percentage as official. Because weights are not published, treat all objectives as important and let the practice questions show you where you are weak.

## Exam Objectives

The 004 exam covers eight objective areas. This plan uses one phase per objective.

- [ ] 1. Infrastructure as Code (IaC) with Terraform
- [ ] 2. Terraform fundamentals
- [ ] 3. Core Terraform workflow
- [ ] 4. Terraform configuration
- [ ] 5. Terraform modules
- [ ] 6. Terraform state management
- [ ] 7. Maintain infrastructure with Terraform
- [ ] 8. HCP Terraform

## Progress Tracker

- [ ] Phase 0 Setup and orientation
- [ ] Phase 1 Infrastructure as Code with Terraform
- [ ] Phase 2 Terraform fundamentals
- [ ] Phase 3 Core Terraform workflow
- [ ] Phase 4 Terraform configuration
- [ ] Phase 5 Terraform modules
- [ ] Phase 6 Terraform state management
- [ ] Phase 7 Maintain infrastructure with Terraform
- [ ] Phase 8 HCP Terraform
- [ ] Phase 9 Practice and review
- [ ] Phase 10 Final review
- [ ] Exam day

---

## Phase 0: Setup and orientation

Goal: get a working environment and read the official scope before studying any single topic.

- [ ] Read the official Terraform Associate 004 exam page end to end
- [ ] Read the official Exam Content List for 004 so you know the exact wording of every objective
- [ ] Install Terraform and confirm the version with `terraform version`
- [ ] Set up a free cloud account you are comfortable creating throwaway resources in, or use the `random` and `local` providers to practice without cloud cost
- [ ] Create a scratch directory where you will build and tear down practice configurations
- [ ] Bookmark the Terraform Registry and the CLI documentation

Readiness gate: you can run `terraform version` and you can state, in one sentence, what the exam is testing.

---

## Phase 1: Infrastructure as Code (IaC) with Terraform

Goal: understand the conceptual case for IaC and Terraform's position in it.

Official sub-objectives: 1a explain what IaC is, 1b describe the advantages of IaC patterns, 1c explain how Terraform manages multi-cloud, hybrid cloud, and service-agnostic workflows.

### Concepts to master

- [ ] What Infrastructure as Code is
- [ ] The advantages of IaC patterns: versioning, repeatability, automation, reduced drift, peer review
- [ ] How Terraform enables multi-cloud, hybrid cloud, and service-agnostic workflows
- [ ] How Terraform differs from configuration management tools that focus on in-place mutation
- [ ] Declarative versus imperative approaches, and why Terraform is declarative

### Tasks

- [ ] Write in your own words why IaC reduces configuration drift
- [ ] List three concrete advantages of IaC you could cite in an exam scenario

Readiness gate: you can explain to a non-expert why a team would adopt Terraform.

---

## Phase 2: Terraform fundamentals

Goal: providers, and a first mental model of state.

Official sub-objectives: 2a install and version Terraform providers, 2b describe how Terraform uses providers, 2c write Terraform configuration using multiple providers, 2d explain how Terraform uses and manages state.

### Concepts to master

- [ ] What a provider is and how Terraform uses providers to talk to APIs
- [ ] How to install providers and how Terraform pins and versions them
- [ ] The role of the `required_providers` block and version constraints
- [ ] Writing a configuration that uses more than one provider
- [ ] Provider configuration and provider aliases for multiple instances
- [ ] A first understanding of what Terraform state is and why Terraform needs it

### Tasks

- [ ] Write a configuration with two providers and run `terraform init` to see them install
- [ ] Pin a provider to a specific version constraint and observe the lock file `.terraform.lock.hcl`
- [ ] Add a second instance of a provider using an alias and reference it from a resource

Readiness gate: you can explain the difference between Terraform core and a provider, and what `terraform init` downloads.

---

## Phase 3: Core Terraform workflow

Goal: the day-to-day command workflow. This is the most hands-on objective.

Official sub-objectives: 3a describe the Terraform workflow, 3b initialize a working directory, 3c validate a configuration, 3d generate and review an execution plan, 3e apply changes to infrastructure, 3f destroy Terraform-managed infrastructure, 3g apply formatting and style adjustments.

### Concepts to master

- [ ] The core workflow: write, then plan, then apply
- [ ] `terraform init` and what it sets up
- [ ] `terraform validate` and what it does and does not check
- [ ] `terraform plan` and how to read an execution plan, including add, change, and destroy markers
- [ ] `terraform apply`, including auto-approve and the approval prompt
- [ ] `terraform destroy` and targeted destroy
- [ ] `terraform fmt` for formatting and style

### Tasks

- [ ] Run a full init, plan, apply, destroy cycle on a real or simulated resource
- [ ] Read a plan output and identify which resources will be created, changed, or destroyed
- [ ] Intentionally write malformed configuration and see what `terraform validate` reports
- [ ] Run `terraform fmt` on a messy file and observe the changes

Readiness gate: you can describe, from memory and in order, what each core command does and when you would run it.

---

## Phase 4: Terraform configuration

Goal: the largest concept surface. HCL language features, variables, expressions, dependencies, and sensitive data.

Official sub-objectives: 4a use and differentiate `resource` and `data` blocks, 4b refer to resource attributes and create cross-resource references, 4c use variables and outputs, 4d understand and use complex types, 4e write dynamic configuration using expressions and functions, 4f define resource dependencies, 4g validate configuration using custom conditions, 4h understand best practices for managing sensitive data including secrets management with Vault.

### Concepts to master

- [ ] The difference between a `resource` block and a `data` block
- [ ] Referencing resource attributes and creating cross-resource references
- [ ] Input variables, including type constraints, defaults, and validation
- [ ] Output values and what they expose
- [ ] Local values
- [ ] Complex types: list, set, map, object, and tuple
- [ ] Expressions and built-in functions for dynamic configuration
- [ ] `count` and `for_each` for multiple instances
- [ ] Implicit dependencies via references, and explicit dependencies via `depends_on`
- [ ] Custom conditions: variable `validation`, `precondition`, and `postcondition`
- [ ] Best practices for sensitive data, including marking values `sensitive` and secrets management with Vault

### Tasks

- [ ] Use a `data` source and feed its output into a `resource`
- [ ] Build a configuration driven entirely by variables, with at least one validation rule
- [ ] Use `for_each` over a map to create several similar resources
- [ ] Add an explicit `depends_on` and explain why the implicit reference was not enough
- [ ] Mark an output as `sensitive` and observe how Terraform hides it
- [ ] Write one `precondition` or `postcondition` and trigger it on purpose

Readiness gate: you can build a parameterized configuration with complex types and dependencies without copying from docs.

---

## Phase 5: Terraform modules

Goal: how Terraform finds, scopes, and versions modules.

Official sub-objectives: 5a explain how Terraform sources modules, 5b describe variable scope within modules, 5c use modules in configuration, 5d manage module versions.

### Concepts to master

- [ ] How Terraform sources modules: local paths, the registry, and remote sources
- [ ] The root module versus child modules
- [ ] Variable scope within modules, and that child modules do not see parent variables unless passed
- [ ] Passing inputs into a module and reading its outputs
- [ ] Managing module versions with the `version` argument for registry modules

### Tasks

- [ ] Refactor a flat configuration into a root module plus one child module
- [ ] Call a public registry module and pin it to a version
- [ ] Pass an input into a module and consume one of its outputs in the root

Readiness gate: you can explain why a value defined in the root is not automatically visible inside a child module.

---

## Phase 6: Terraform state management

Goal: backends, locking, remote state, and drift.

Official sub-objectives: 6a describe the local backend, 6b describe state locking, 6c configure remote state using the backend block, 6d manage resource drift and Terraform state.

### Concepts to master

- [ ] The local backend and where state lives by default
- [ ] State locking and why it prevents concurrent corruption
- [ ] Configuring remote state with the `backend` block
- [ ] What resource drift is and how Terraform detects it on the next plan
- [ ] State commands at a high level: `terraform state list`, `show`, `mv`, and `rm`
- [ ] Why the state file can contain sensitive data and must be protected

### Tasks

- [ ] Inspect a local state file and identify what it stores
- [ ] Configure a remote backend, even a simulated or free-tier one, and migrate state to it
- [ ] Change a resource outside Terraform, then run `terraform plan` and observe the detected drift
- [ ] Use `terraform state list` and `terraform state show` to inspect managed resources

Readiness gate: you can explain why two engineers running apply at the same time is dangerous without state locking.

---

## Phase 7: Maintain infrastructure with Terraform

Goal: bringing existing infrastructure under management and debugging.

Official sub-objectives: 7a import existing infrastructure into your workspace, 7b use the CLI to inspect state, 7c describe when and how to use verbose logging.

### Concepts to master

- [ ] Importing existing infrastructure with `terraform import` or `import` blocks
- [ ] Using the CLI to inspect state for maintenance
- [ ] When and how to use verbose logging with the `TF_LOG` environment variable
- [ ] The general idea of replacing a resource with `-replace` rather than tainting

### Tasks

- [ ] Create a resource outside Terraform, then import it and write matching configuration
- [ ] Set `TF_LOG` to a verbose level and read a portion of the debug output
- [ ] Use `-replace` on a plan to force recreation of one resource

Readiness gate: you can take an unmanaged resource and bring it under Terraform management.

---

## Phase 8: HCP Terraform

Goal: the managed platform and its collaboration and governance features, at the level the exam describes them.

Official sub-objectives: 8a use HCP Terraform to create infrastructure, 8b describe HCP Terraform collaboration and governance features, 8c describe how to organize and use HCP Terraform workspaces and projects, 8d configure and use HCP Terraform integration.

### Concepts to master

- [ ] What HCP Terraform is and how it runs Terraform for you
- [ ] Using HCP Terraform to create infrastructure
- [ ] Collaboration and governance features at a descriptive level
- [ ] Organizing work with workspaces and projects
- [ ] Configuring an HCP Terraform integration, including remote runs and remote state

### Tasks

- [ ] Create a free HCP Terraform organization and a workspace
- [ ] Connect a configuration to HCP Terraform and trigger a remote run
- [ ] Read how workspaces and projects organize state and access

Readiness gate: you can describe what HCP Terraform adds over running Terraform locally.

---

## Phase 9: Practice and review

Goal: convert knowledge into exam performance.

- [ ] Work through the [official Sample Questions for 004](https://developer.hashicorp.com/terraform/tutorials/certification-004/associate-questions-004) to learn the three question formats
- [ ] Walk the [official Study Guide for 004](https://developer.hashicorp.com/terraform/tutorials/certification-004/associate-study-004) and confirm every linked topic is checked above
- [ ] Use the [official Exam Review list for 004](https://developer.hashicorp.com/terraform/tutorials/certification-004/associate-review-004) as a final gap audit, sub-objective by sub-objective
- [ ] Take any reputable practice exam and review every wrong answer in your own words
- [ ] Re-drill the two objectives where you scored lowest
- [ ] Confirm every objective in the tracker at the top is checked

---

## Phase 10: Final review

Goal: consolidate, do not learn anything new.

- [ ] Reread the official Exam Content List one final time
- [ ] Review your notes on wrong practice answers
- [ ] Skim the core CLI commands and confirm you can describe each from memory
- [ ] Do not study new material the day before
- [ ] Get a full night of sleep

---

## Exam Day

- [ ] Confirm your testing environment meets the online proctoring requirements
- [ ] Have your ID ready and a clear workspace as required by the proctor
- [ ] Pace yourself across the hour and flag hard questions to revisit
- [ ] Take the exam

---

## Out of Scope

These are not required for the Associate 004 exam. Do not sink time into them now.

- [ ] Writing custom providers with the plugin framework or Go SDK
- [ ] Authoring Sentinel or OPA policy as code in depth, beyond describing that governance exists
- [ ] The CDK for Terraform (CDKTF)
- [ ] Deep dives into Vault, Consul, Nomad, or Packer as separate products
- [ ] Memorizing the full resource catalog of any single cloud provider
- [ ] Terraform Enterprise installation and operations
- [ ] Advanced provider development and testing frameworks

---

## Resources

### Official HashiCorp

- [Terraform Associate (004) certification details](https://developer.hashicorp.com/certifications/infrastructure-automation#terraform-associate-(004)-details)
- [Terraform certification 004 tutorial track](https://developer.hashicorp.com/terraform/tutorials/certification-004)
- [Terraform documentation](https://developer.hashicorp.com/terraform/docs)
- [Terraform Registry](https://registry.terraform.io)
- [HCP Terraform](https://app.terraform.io)

### Tutorial track contents

- [ ] [Study Guide for Terraform Associate 004](https://developer.hashicorp.com/terraform/tutorials/certification-004/associate-study-004), the curated guide with per-objective tutorials and docs
- [ ] [Exam Review for 004](https://developer.hashicorp.com/terraform/tutorials/certification-004/associate-review-004), the verbatim sub-objective checklist
- [ ] [Sample Questions for 004](https://developer.hashicorp.com/terraform/tutorials/certification-004/associate-questions-004), five examples covering the three question formats
