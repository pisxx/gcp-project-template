## gcp-project-factory (GitHub template)

Self‑service **GCP lab project provisioning** via GitHub template repo + GitHub Actions.

- **dev UX**: create repo from template → edit `config.yaml` → run workflow → get a GCP project
- **governance**: projects under a dedicated `LABS` folder, with budget + baseline policy/IAM
- **security**: GitHub OIDC → **Workload Identity Federation** (no JSON keys)

### How to use (intended flow)

- **Create repo**: click **Use this template** in GitHub
- **Configure**: edit `config.yaml`
- **Provision**: run “Provision Lab Project” workflow (Actions tab)
- **Destroy**: run “Destroy Lab Project” workflow

> Note: this repo is being bootstrapped as a template first. Workflows/scripts are added next.

### `config.yaml` (required fields only)

```yaml
project:
  name: "payments-lab"

users:
  owners:
    - "dev1@company.com"
  editors:
    - "dev2@company.com"
  viewers: []
```

### Naming + validation (planned)

- **project id**: derived from `project.name` + repo context (stable hash) to avoid collisions
- **validation**: allowed chars/length + enforced prefix (e.g. `lab-*`)
- **SSO**: only corporate identities (e.g. `@company.com`) accepted in `users.*`

### What the provisioning does (target behavior)

- **create project** in `folders/DEVS_LABS_FOLDER_ID` (folder name: `devs-labs`)
- **link billing** (lab billing account)
- **set budget** (hardcoded defaults; increases via request)
- **region**: hardcoded `us-central1`
- **enable baseline APIs** (hardcoded list for now)
- **apply IAM** for `users.*`

### Budget increase

- **Request**: open an issue (use “Lab project request”) and include the requested budget amount + justification

### Repo contents (template)

- `config.yaml` (project request)
- `.github/` (issue + PR templates)
- `.github/workflows/` (to be added) provision/destroy workflows
- `scripts/` (to be added) minimal `gcloud`-based provisioning

### Contributing

- **Change request**: open a PR using the PR template
- **New feature**: open an issue using the “Feature request” template
# gcp-project-template
# gcp-project-factory
# gcp-project-template
# gcp-project-template
