# GitHub Actions Workflow Triggers

GitHub Actions workflows activate through various events from GitHub activity, schedules, manual inputs, or external signals. Core triggers include `push`, `pull_request`, `schedule`, and `workflow_dispatch`.

## Common Triggers

### push
- Fires on commits pushed to branches/tags or repo template creation.
- Use case: Run builds/tests per code change for quality checks.

### pull_request
- Activates on PR open/edit/sync/close events.
- Use case: Automated testing/linting before main branch merge.

### schedule
- Uses POSIX cron syntax for UTC-timed runs.
- Use case: Nightly builds, reports, cleanup tasks.

### workflow_dispatch
- Manual trigger via GitHub UI/CLI/REST API with runtime inputs.
- Use case: Deploy to staging/prod with custom parameters.

## Other Key Events

- **issues**: Triggers on issue open/edit/delete/label changes.
- **release**: Fires on release draft/publish/update.
- **repository_dispatch**: External POST API trigger for custom integrations.
- **workflow_run**: Chains workflows based on another’s completion.

## YAML Examples
```yaml
on:
  push:
    branches: [main]
  pull_request:
    branches: [main]
  schedule:
    - cron: '0 2 * * *'  # Nightly at 2AM UTC
  workflow_dispatch:
    inputs:
      env:
        description: 'Target env'
        required: true
```

## Trigger Summary Table
| Trigger | Source | Best For |
|---------|--------|----------|
| push | Git pushes | CI on commits |
| pull_request | PR activity | PR validation |
| schedule | Cron | Periodic tasks |
| workflow_dispatch | Manual/API | On-demand deploys |
| repository_dispatch | External POST | Integrations |
| workflow_run | Other workflows | Chained automation |
