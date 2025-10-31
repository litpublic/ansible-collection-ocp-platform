# Argo Bootstrap Role

Bootstraps OpenShift GitOps (Argo CD) by subscribing to the operator, creating an instance, and seeding a skeleton App-of-Apps tree.

## Usage

```yaml
- hosts: localhost
  gather_facts: false
  roles:
    - role: litpublic.ocp_platform.argo_bootstrap
      vars:
        argo_bootstrap_apply_resources: true
        argo_namespace: openshift-gitops
        gitops_repo_url: https://git.example.com/platform/gitops-seed.git
        gitops_repo_revision: main
        gitops_app_of_apps_path: apps/app-of-apps
```

## Variables

- `argo_bootstrap_apply_resources`: master switch to apply Kubernetes manifests (default: `true`)
- `argo_namespace`: namespace where the operator instance and manifests are placed (default: `openshift-gitops`)
- `gitops_repo_url`: Git repository cloned by the App-of-Apps (default: `https://git.example.com/platform/gitops-seed.git`)
- `gitops_repo_revision`: branch or tag checked out by the App-of-Apps (default: `main`)
- `gitops_app_of_apps_path`: path within the repo that contains the App-of-Apps definition (default: `apps/app-of-apps`)
