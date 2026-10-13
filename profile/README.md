<img src="https://raw.githubusercontent.com/reflex-automation/.github/main/profile/reflex-logo.svg" alt="Reflex" width="220">

Reflex is a community-maintained continuation of Event-Driven Ansible
(EDA) that targets open-source AWX-compatible controllers, mainly
[CIQ Ascender](https://ciq.com/products/ascender).

ansible/eda-server and ansible/ansible-ui are actively developed by Red
Hat. Reflex tracks them as friendly forks: the patch set stays small,
upstream merges happen regularly, CVEs get patched, and every release is
smoke-tested end to end against Ascender: a webhook-triggered rulebook
activation launches a real job template.

ansible/eda-server-operator is not really maintained (ingress bugs sat
unfixed), so reflex-operator is an independent fork and no longer syncs
from upstream.

Internal identifiers (`aap_eda`, `/api/eda/v1`, `EDA_*` settings) keep
their upstream names so merges stay clean, the same model Ascender uses
with AWX.

## Repos

| Repo | Role | Forked from |
|---|---|---|
| [reflex-server](https://github.com/reflex-automation/reflex-server) | API server, workers, scheduler | [ansible/eda-server](https://github.com/ansible/eda-server) |
| [reflex-ui](https://github.com/reflex-automation/reflex-ui) | Web UI | [ansible/ansible-ui](https://github.com/ansible/ansible-ui) |
| [reflex-operator](https://github.com/reflex-automation/reflex-operator) | Kubernetes operator | [ansible/eda-server-operator](https://github.com/ansible/eda-server-operator) |
| [reflex-decision-environment](https://github.com/reflex-automation/reflex-decision-environment) | Decision environment container image | none (not a fork) |

[ansible-rulebook](https://github.com/ansible/ansible-rulebook) is not
forked; Red Hat still maintains it. It's pinned in the decision
environment image.

## What Reflex adds

- Standalone login: `RESOURCE_SERVER__URL` defaults to empty, so session login works without an AAP gateway.
- Suggest-only activations: rules evaluate and show in the rule audit, but job template, workflow, playbook and module actions only log a debug message. Use it to dry-run a rulebook against live events.
- Prometheus metrics at `/api/eda/v1/metrics/` (activations, event streams, rule audit, request queue), for superusers or a bearer token set in `EDA_METRICS_TOKEN`.
- Project push webhooks: a git host push to `/api/eda/v1/external_project/<uuid>/post/` syncs the project. Uses a GitHub, GitLab, HMAC or Token event stream credential.
- Releases smoke-tested end to end against Ascender.

## Getting started

Deploy on Kubernetes with
[reflex-operator](https://github.com/reflex-automation/reflex-operator).
Container images are published at `ghcr.io/reflex-automation`.
