# \[Work In Progress\] AMWA IN-003: Compute Resource Management Manifest and Examples

[![Lint Status](https://github.com/AMWA-TV/in-003/actions/workflows/lint.yml/badge.svg)](https://github.com/AMWA-TV/in-003/actions/workflows/lint.yml)
[![Zensical Render Status](https://github.com/AMWA-TV/in-003/actions/workflows/docs.yml/badge.svg)](https://github.com/AMWA-TV/in-003/actions/workflows/docs.yml)
[![License](https://img.shields.io/github/license/AMWA-TV/in-003)](https://github.com/AMWA-TV/in-003/blob/HEAD/LICENSE)
[![Issues](https://img.shields.io/github/issues/AMWA-TV/in-003)](https://github.com/AMWA-TV/in-003/issues)

This repository holds the source of a work artifact published as an **AMWA Increment (IN)** from the [Advanced Media Workflow Association](https://amwa.tv)

<!-- INTRO-START -->

### What does it do?

- Defines a common, platform-agnostic description of the compute, memory, storage, network, and accelerator resources required by a Media Function.
- Provides a manifest schema and working examples for expressing those resource requirements in a portable way.
- Connects profiling, benchmarking, and deployment workflows into a repeatable CRM process.

### Why does it matter?

- Media Function workloads need predictable resource allocation across heterogeneous infrastructure.
- A standardized manifest helps orchestration systems place workloads accurately and validate resource availability.
- It enables consistent, interoperable resource declarations across vendor implementations and deployment environments.

CRM links design-time resource specification with runtime orchestration, deployment, and operational monitoring across four 
primary architectural tiers as presented in the [JT-DMF-High-Level.pdf](./docs/JT-DMF-High-Level.pdf):

- The repository defines a resource manifest model and example payloads for Media Functions.
- It shows how profiling and benchmarking results can be translated into portable declarations of required resources.
- The resulting manifests can be consumed by orchestration and deployment systems to validate placement and scheduling decisions.

**Media Functions Tier:** Standardizes core logic into discrete Media Functions. Defines the overall **Media Function Descriptor** and the primary **Manifests Schema** (the contract definition).

**Container Platform Tier:** Receives active **Manifests** consumed by dedicated **Operator(s)** to instantiate the **Media Processing Workload**. As the workload executes, it emits **Media Function Metrics** to monitor real-time performance.

**Host Platform Tier:** Exposes underlying physical hardware capabilities via **System Specifications** to inform scheduling decisions.

**Orchestration & Monitoring:** Cross-tier services responsible for evaluating host specifications against manifest requirements, selecting execution environments, and tracking runtime metrics.

## Purpose of This Repository

The purpose of this repository is to define and demonstrate a standardized approach for creating and using CRM manifests throughout the lifecycle of a Media Function.

It provides examples and guidance for:

1. **Profiling a Media Function**  
   Observing how the Media Function uses compute, memory, storage, network bandwidth, and specialized hardware resources under representative operating conditions.

2. **Benchmarking its performance**  
   Measuring the relationship between allocated resources, workload characteristics, performance, and operational limits.

3. **Producing a CRM manifest**  
   Translating the profiling and benchmarking results into a portable, machine-readable declaration of the resources required by the Media Function.

4. **Deploying the Media Function**  
   Demonstrating how an orchestration layer can consume the manifest, evaluate available infrastructure, select an appropriate execution environment, and deploy the Media Function with the required resources.

## Intended Workflow

The repository supports the following workflow:

```text
Media Function
      |
      v
Profile and Benchmark
      |
      v
Determine Resource Requirements
      |
      v
Produce CRM Manifest
      |
      v
Orchestration Layer
      |
      v
Validate, Place, and Deploy
      |
      v
Monitoring
```

This approach allows resource requirements to be based on measured behavior rather than assumptions or platform-specific deployment configurations.

## Benefits

Using a standardized CRM manifest enables:
- Vendors to describe resource requirements independently of the target platform.
- Orchestrators to make informed placement and scheduling decisions.
- Media Functions to be deployed consistently across heterogeneous infrastructure.
- Infrastructure providers to validate resource availability before deployment.
- Operators to achieve more predictable performance and resource utilization.
- The media industry to improve interoperability between Media Functions, platforms, and orchestration systems.

## Scope

This repository contains:
- CRM manifest definitions and supporting models.
- Example resource manifests for Media Functions.
- Examples of profiling and benchmarking methodologies.
- Guidance for translating benchmark results into resource declarations.
- Examples showing how an orchestration layer can consume a CRM manifest.
- Demonstrations of manifest-based validation, placement, and deployment.

The CRM manifest does not prescribe how an orchestration platform must be implemented. Instead, it provides a common resource description that different orchestration systems can interpret and map to their own infrastructure and deployment models.

## Repository Layout

- documentation/: Supporting/legacy background material.
- manifest/: Resource manifests and schema.
- lib/: Code and submodules, including lib/mxl.
- examples/: Runtime examples and deployment assets.

This work artifact is published as an **AMWA Increment (IN)**. Increments are intended to make public the ongoing progress of a working group without locking decisions into a formal specification. While the technical details contained in this repository do not constitute a stable or finalized specification, readers should note that Increments are Draft Specifications as defined in the AMWA IPR Policy. The provisions of the policy apply, including the requirement for early disclosure. You can expect the content to evolve incrementally based on ongoing testing, consensus-building, and community input. Public review is encouraged! Please post an Issue to the Repo to submit questions, feedback, or propose changes.

<!-- INTRO-END -->

