# GitHub Actions Components

- **GitHub Actions Overview**: CI/CD platform for automating build, test, deployment pipelines via YAML files in `.github/workflows/`.

- **Core Components**:
  - **Workflows**:
    - Highest-level container for automation.
    - YAML-defined in repo's `.github/workflows/` directory.
    - Triggered by events (push, pull_request, schedule).
    - Multiple per repo (e.g., CI vs. deployment workflows).
  
  - **Jobs**:
    - Groups of steps executing on same runner (VM/container).
    - Run parallel by default; use `needs` for sequential dependencies.
    - Fresh runner instance per job (no shared filesystem unless artifacts used).
  
  - **Steps**:
    - Individual tasks within a job, executed sequentially.
    - `run`: Shell commands/scripts (e.g., `npm test`).
    - `uses`: Marketplace actions (e.g., `actions/checkout@v4`).
    - Share runner environment/filesystem within same job.

- **Execution Hierarchy**:
  ```
  Workflow → Contains Jobs → Contains Steps → Contains Actions/Commands
  ```

- **Key Relationships**:
  | Component | Runs On | Contains |
  |-----------|---------|----------|
  | Workflow | N/A | 1+ Jobs |
  | Job | 1 Runner | 1+ Steps |
  | Step | Job's Runner | Commands/Actions |
