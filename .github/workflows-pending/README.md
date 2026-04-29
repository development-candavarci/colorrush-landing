# Secret Scan Workflow — Pending Install

Bu repo gitleaks tabanli secret leak taramasi icin hazirlandi.

## CEO Install (workflow scope gerekli, tek defa)

GitHub PAT'a `workflow` scope ekledikten sonra (https://github.com/settings/tokens):

```bash
gh api -X PUT \
  "repos/development-candavarci/REPO_NAME/contents/.github/workflows/secret-scan.yml" \
  -f "message=feat(P1.8): activate gitleaks secret-scan workflow" \
  -f "content=$(base64 -i .github/workflows-pending/secret-scan.yml | tr -d '\n')" \
  -f "branch=main"
```

Aktive ettikten sonra her push + PR'da gitleaks otomatik tarar.
Secret leak bulursa CI fail eder, ek koruma katmani.

Pending dosyayi temizle (workflow aktive olduktan sonra):

```bash
gh api -X DELETE \
  "repos/development-candavarci/REPO_NAME/contents/.github/workflows-pending/secret-scan.yml" \
  -f "message=cleanup: remove pending workflow stub" \
  -f "branch=main" \
  -f "sha=PENDING_FILE_SHA"
```
