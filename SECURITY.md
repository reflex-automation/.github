# Security policy

## Reporting a vulnerability

Use GitHub's private vulnerability reporting: open the Security tab of the affected repo and click "Report a vulnerability". Please don't open a public issue for security problems.

This policy covers all reflex-automation repos: reflex-server, reflex-operator, reflex-ui, and reflex-decision-environment.

## Supported versions

Only the latest images are supported: `ghcr.io/reflex-automation/{reflex-server,reflex-ui,reflex-operator}:main` and the current reflex-decision-environment tag. There are no maintained release branches.

## What to expect

This is a small community project with no SLA. Reports get a reply within a week, usually sooner. Fixes for confirmed issues land on main and ship in the next image build.

Known CVEs in dependencies are tracked automatically (Dependabot and Trivy image scans), so a report is most useful for issues in the code itself or for a dependency CVE that looks exploitable in a real deployment.
