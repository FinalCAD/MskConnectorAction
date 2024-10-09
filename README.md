# MskConnectorAction

Github Action to apply msk connectors based on yaml file.
Those files must validate against `cue` schema.

## Inputs

### `aws-role`
[**Required**] AWS role allowing Secret manager usage

### `aws-region`
AWS region for ECR checks, Default: eu-central-1

### `terraform-version`
Terraform version to use, Default: latest

### `terragrunt-version`
Terragrunt version to use, Default: latest

### `terraform-data-one-repo`
Repository containing terraform code for glue creation, Default: FinalCAD/terraform-data-one-repo

### `terraform-data-one-ref`
Reference to use for `terraform-data-one-repo` repository, Default: master

### `github-token`
Github token to avoid limit rate when pulling package

### `github-ssh`
[**Required**] Github ssh key to pull `terraform-data-one-repo` repository

### `environment`
[**Required**] Finalcad envrionment: production, staging, sandbox

### `region-friendly`
Finalcad region: frankfurt or tokyo, Default: frankfurt

### `config-file-prefix`
Sub path for glue configuration file, default: 'configuration'

### `pr-number`
Action launch from a pull_request, only excute plan, default ''.

## Usage

```yaml
  - name: Deploy msk connector job sandbox
    uses: FinalCAD/MskConnectorAction@v2
    with:
      github-ssh: ${{ secrets.GH_DEPLOY_SSH }}
      environment: sandbox
      aws-role: ${{ secrets.DEPLOY_ROLE_MASTER }}
      github-token: ${{ secrets.GH_PACKAGES_READ }}
```
