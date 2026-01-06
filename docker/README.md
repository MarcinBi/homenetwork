# Docker Stacks

This directory contains documentation and configuration templates for Docker-based services running in the homelab.

---

## Philosophy

- documentation first
- templates only (no secrets or runtime data)
- each service is self-contained
- incremental improvement over time

---

## Structure

```text
docker/
  stacks/
    <service-name>/
      README.md
      compose.yaml        # sanitized
      env.template        # example values only

