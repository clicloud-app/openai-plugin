# CLI for ChatGPT

CLI lets the model deploy and run your apps, workers, databases, static sites and functions on
[CLI](https://clicloud.app). It can create services from a GitHub repository, set non-secret
variables, deploy, read logs and metrics, roll back, manage domains and backups, and check whether
an app is ready for real traffic. Every change is recorded in CLI's activity log.

## What it connects to

The plugin uses CLI's hosted MCP server at `https://api.clicloud.app/mcp/openai` over HTTPS. You sign in to CLI with
OAuth and choose which projects it can use and how much it may spend a day.

## What it sends and can't do

- It sends CLI only the arguments of each tool call and the one-sentence reason for each change.
- It never takes API keys or passwords: those are entered in the CLI dashboard, and tools return a
  link for them.
- It doesn't start payments, sell credits or link to checkout. Credit is added in the CLI dashboard.

Privacy: https://clicloud.app/privacy · Terms: https://clicloud.app/terms · Support: support@clicloud.app
