# Splat Runner

## Overview

This repository is dedicated to hosting our configuration files and schedules for running [Splat](https://github.com/gira-de/splat).

Splat is a tool designed to automate the auditing and potentially automatically fixing security issues in code repositories.

## Environment Variables

This repo requires the following environment variables to function properly:

| Variable                          | Description                                                                                                                                    |
| --------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------- |
| `SPLAT_GITHUB_USER_ACCESS_TOKEN`  | This token is needed by Splat to access all the projects that are accessible to user that this access token belongs to.                        |
| `SPLAT_TEAMS_WEBHOOK_URL` | This URL is used for sending notifications to Microsoft Teams.                                                                                 |

## Local Execution

To test this deployment of Splat locally, follow these steps:

1. Install [act](https://github.com/nektos/act) (runs GitHub Actions locally via Docker)

2. Create a file ".secrets" (which is git-ignored) where you put valid values for your test configuration:

**.secrets:**

```bash
SPLAT_TEAMS_WEBHOOK_URL=<webhook-url>
SPLAT_GITHUB_USER_ACCESS_TOKEN=<some-access-token>
```

**Important!** Note that splat will run on _all_ projects that the access token has access to. If you want it to run on specific projects only, modify the `splat.yaml` and temporarily add a filter.

3. Run Splat locally
```bash
act workflow_dispatch
```
