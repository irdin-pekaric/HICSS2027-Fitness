# Beyond FAIR: Fitness Functions for Sustainable Research Software

This repository accompanies the anonymized paper _"Beyond FAIR: A Fitness Function Framework for Sustainable Research Software"_.

The repository contains a lightweight and modular prototype for assessing sustainability properties of research software artifacts **beyond the traditional FAIR dimensions**. While FAIR remains important for findability, accessibility, interoperability, and reusability, this prototype focuses on additional sustainability concerns related to:

- **Environmental responsibility**, including resource efficiency, execution footprint, infrastructure awareness, and recomputation avoidance.
- **Long-term security**, including dependency health, secure configuration, integrity/provenance, and maintainable security posture.

Each checker is implemented as an independent notebook and produces a corresponding JSON result file. The goal is to make sustainability properties measurable, transparent, and easy to evaluate for research software repositories.

---

## Repository Overview

The repository includes one metadata file, eight checker notebooks, and eight corresponding result files.

<pre>
.
├── artifacts.json
├── dependency_health_checker.ipynb
├── dependency_health_results.json
├── footprint_transparency_checker.ipynb
├── footprint_transparency_results.json
├── infrastructure_awareness_checker.ipynb
├── infrastructure_awareness_results.json
├── integrity_provenance_checker.ipynb
├── integrity_provenance_results.json
├── maintainable_security_checker.ipynb
├── maintainable_security_results.json
├── recomputation_avoidance_checker.ipynb
├── recomputation_avoidance_results.json
├── resource_efficiency.ipynb
├── resource_efficiency_results.json
├── secure_configuration_checker.ipynb
├── secure_configuration_results.json
└── README.md
</pre>

---

## Input Metadata

The file `artifacts.json` contains the metadata of the research software artifacts evaluated by the prototype. Each artifact entry can include information such as:

- artifact title,
- repository URL,
- short description,
- relevant metadata needed by the checkers.

The checkers use this file as their main input source.

---

## Environmental Sustainability Checkers

### Resource Efficiency Checker

The `resource_efficiency.ipynb` notebook evaluates whether a research software artifact stays within predefined resource thresholds during a benchmarked execution.

The checker may inspect indicators such as:

- repository size,
- number of files,
- number of dependencies,
- execution time,
- peak memory consumption.

The corresponding output is stored in:

```text
resource_efficiency_results.json
```

This checker helps make computational cost visible and supports a first assessment of whether an artifact can be executed with limited resource overhead.

---

### Footprint Transparency Checker

The `footprint_transparency_checker.ipynb` notebook evaluates whether an artifact provides sufficient information about its execution footprint.

The checker looks for evidence such as:

- README documentation,
- dependency files,
- runtime or installation requirements,
- platform or hardware requirements,
- container or deployment information.

The corresponding output is stored in:

```text
footprint_transparency_results.json
```

This checker supports responsible artifact reuse by assessing whether users can understand the expected execution conditions before running the software.

---

### Infrastructure Awareness Checker

The `infrastructure_awareness_checker.ipynb` notebook evaluates whether an artifact can be deployed without unnecessary infrastructure burden.

The checker may inspect whether the repository shows evidence of:

- low dependency overhead,
- absence of unnecessary hardware specialization,
- absence of hard-coded platform assumptions,
- absence of privileged execution requirements,
- portability across common environments.

The corresponding output is stored in:

```text
infrastructure_awareness_results.json
```

This checker helps identify whether software can be executed in standard environments without avoidable environmental or deployment costs.

---

### Recomputation Avoidance Checker

The `recomputation_avoidance_checker.ipynb` notebook evaluates whether an artifact supports mechanisms that reduce unnecessary repeated computation.

The checker looks for evidence such as:

- caching,
- checkpointing,
- modular execution,
- parameterized workflows,
- reusable intermediate results,
- documented rerun procedures.

The corresponding output is stored in:

```text
recomputation_avoidance_results.json
```

This checker highlights whether an artifact helps users avoid wasteful recomputation when reproducing or extending research results.

---

## Security Sustainability Checkers

### Dependency Health Checker

The `dependency_health_checker.ipynb` notebook evaluates whether an artifact relies on declared, manageable, and maintainable dependencies.

The checker may inspect:

- dependency files,
- version constraints,
- pinned or bounded dependencies,
- potentially risky dependency patterns,
- evidence of outdated or difficult-to-maintain dependency structures.

The corresponding output is stored in:

```text
dependency_health_results.json
```

This checker supports long-term sustainability by assessing whether external software components can be maintained and updated with reasonable effort.

---

### Secure Configuration Checker

The `secure_configuration_checker.ipynb` notebook evaluates whether an artifact exposes insecure defaults or unsafe operational patterns.

The checker looks for possible issues such as:

- hard-coded secrets,
- exposed API keys,
- unsafe debug settings,
- disabled SSL/TLS verification,
- plaintext communication settings,
- overly permissive configuration,
- committed sensitive files.

The corresponding output is stored in:

```text
secure_configuration_results.json
```

This checker is intended as a lightweight diagnostic mechanism. It does not replace a full security audit, but it can reveal common configuration risks early.

---

### Integrity and Provenance Checker

The `integrity_provenance_checker.ipynb` notebook evaluates whether an artifact supports traceability and verifiability over time.

The checker may inspect evidence such as:

- Git metadata,
- commit information,
- dependency files,
- version pinning,
- license files,
- citation metadata,
- release metadata,
- checksums,
- container or lock files.

The corresponding output is stored in:

```text
integrity_provenance_results.json
```

This checker helps assess whether an artifact and its execution environment can be traced, verified, and trusted over time.

---

### Maintainable Security Checker

The `maintainable_security_checker.ipynb` notebook evaluates whether an artifact provides evidence that security issues can be detected, reported, and remediated over time.

The checker looks for evidence such as:

- security policy files,
- automated dependency updates,
- security workflows,
- continuous integration workflows,
- static-analysis tooling,
- test directories,
- issue templates,
- governance or maintenance files,
- release metadata.

The corresponding output is stored in:

```text
maintainable_security_results.json
```

This checker focuses on the long-term security posture of research software and highlights whether security maintenance can be performed systematically.

---

## Output Files

Each checker produces a JSON result file. These files contain the diagnostic evidence and pass/fail outcome generated by the corresponding notebook.

The result files are:

```text
dependency_health_results.json
footprint_transparency_results.json
infrastructure_awareness_results.json
integrity_provenance_results.json
maintainable_security_results.json
recomputation_avoidance_results.json
resource_efficiency_results.json
secure_configuration_results.json
```

The JSON outputs are intended to make the results easy to inspect, compare, and reuse in later analysis.

---

## How to Use

1. Add or update artifact metadata in `artifacts.json`.
2. Open the checker notebook you want to execute.
3. Run the notebook cells.
4. Inspect the generated JSON result file.
5. Use the diagnostic output to identify sustainability gaps and possible repository improvements.

The notebooks can be executed independently. This makes it possible to evaluate only one sustainability dimension or to run all checkers as a complete assessment.

---

## Prerequisites

The prototype is designed for standard Python-based research environments.

Recommended requirements:

```text
Python 3.8+
Jupyter Notebook or JupyterLab
requests
packaging
setuptools
```

Additional dependencies may be required depending on the specific checker and the repositories being evaluated.

Install common dependencies with:

```bash
pip install requests packaging setuptools jupyter
```

---

## Purpose

This repository demonstrates how sustainability properties beyond FAIR can be translated into executable fitness functions. The framework is intended to help researchers, artifact evaluators, and repository maintainers identify issues that may affect long-term reuse, responsible execution, and security maintenance.

The prototype should be understood as a lightweight first layer of automated evidence. It is not a replacement for manual review, security auditing, or domain-specific benchmarking, but it provides a practical starting point for making sustainability concerns measurable and actionable.
