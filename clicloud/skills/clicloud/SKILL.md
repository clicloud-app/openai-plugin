---
name: clicloud
description: Deploy and operate apps, databases, static sites and functions on CLI (clicloud.app) with the CLI tools. Use when the user wants something deployed, hosted, scaled, monitored or debugged on CLI.
---

The CLI tools manage the user's CLI account: projects, services (apps, workers, databases, static sites, functions), deploys, non-secret variables, domains, logs, metrics, backups and alerts.

How the tools work:

- Read-only tools are marked read-only. Tools that change something end in `_change` when the same area also has a read-only tool. Tools whose changes can't be undone (deletes, restores, replacing the running version) are marked destructive.
- Every change is recorded in CLI's activity log as made through this app.
- Errors carry `error.code` and `remediation` steps. Follow the remediation, then retry.
- Secrets (API keys, passwords, tokens) are never passed through these tools. When a value looks like a secret, the tool returns a dashboard link where the user enters it. Pass that link to the user.
- These tools can't add credit or make payments. When a project is out of credit, tell the user the project needs more credit; its owner manages credit outside the chat.
- Commands aren't run through these tools: no shell, and scheduled jobs and start commands are set in the CLI dashboard.
- Some changes need a person's approval (the project's rules, or a connection's daily spending limit). The tool returns APPROVAL_REQUIRED; cli_wait_for_approval waits for the answer.
- Long jobs (deploys, backups, restores) answer within about 25 seconds. If the result says `stillRunning`, check again later with the tool named in `next`.

A typical deploy: cli_list_projects, then cli_create_service from a GitHub repo, cli_set_env for non-secret settings, cli_deploy, and cli_deploy_status or cli_logs until it's healthy. Reply with the URL.

To check an app is ready for real traffic, use cli_go_live.
