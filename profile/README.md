<img src="https://raw.githubusercontent.com/reflex-automation/.github/main/profile/reflex-logo.svg" alt="Reflex" width="220">

Reflex is a community-maintained continuation of Event-Driven Ansible
(EDA) that targets open-source AWX-compatible controllers, mainly
[CIQ Ascender](https://ciq.com/products/ascender).

Red Hat stopped developing EDA as a supported open-source product and now
uses the code as the internal upstream of Ansible Automation Platform.
Reflex tracks the ansible/* repos as friendly forks: the patch set stays
small, upstream merges happen regularly, CVEs get patched, and every
release is smoke-tested end to end against Ascender: a webhook-triggered
rulebook activation launches a real job template.

Internal identifiers (`aap_eda`, `/api/eda/v1`, `EDA_*` settings) keep
their upstream names so merges stay clean, the same model Ascender uses
with AWX.

## Repos

| Repo | Role | Forked from |
|---|---|---|
| [reflex-server](https://github.com/reflex-automation/reflex-server) | API server, workers, scheduler | [ansible/eda-server](https://github.com/ansible/eda-server) |
| [reflex-ui](https://github.com/reflex-automation/reflex-ui) | Web UI | [ansible/ansible-ui](https://github.com/ansible/ansible-ui) |
| [reflex-operator](https://github.com/reflex-automation/reflex-operator) | Kubernetes operator | [ansible/eda-server-operator](https://github.com/ansible/eda-server-operator) |
| [reflex-decision-environment](https://github.com/reflex-automation/reflex-decision-environment) | Decision environment container image | — |

[ansible-rulebook](https://github.com/ansible/ansible-rulebook) is not
forked — Red Hat still maintains it. It's pinned in the decision
environment image.

## Getting started

Deploy on Kubernetes with
[reflex-operator](https://github.com/reflex-automation/reflex-operator).
Container images are published at `ghcr.io/reflex-automation`.
