---
name: deploy
description: Deploy a GitHub repository to CLI, watch it go live, and fix it if it fails
---

Deploy the user's repository to CLI with the CLI tools.

1. Call cli_list_projects to find the project (cli_create_project if there's none), then cli_get_project to see what's there.
2. Create an app service from the repository with cli_create_service, unless one already exists for it.
3. Set the non-secret variables the code reads with cli_set_env. For API keys and passwords, give the user the dashboard link the tool returns. If the code expects a database, add one with cli_create_database and connect it with cli_link_database.
4. Deploy with cli_deploy. If it fails, follow the error's remediation, read cli_logs, and deploy again. Stop after three failed tries and explain what's wrong.
5. When it's live, reply with the URL and what you set up.
