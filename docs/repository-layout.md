# Initial Repository Layout

Target structure:

```text
full-stack-dentist/
  README.md
  apps/
    web/
    mobile/
    desktop/
  services/
    api/
    worker/
    policy/
    audit/
    export/
  packages/
    schemas/
    sdk/
    crypto/
    ui/
  protocols/
    registry.yaml
    mappings/
  modules/
    identity/
    vault/
    student/
    credentials/
    truth/
    ai-competition/
    interchange/
    association/
    study-club/
    clinical/
    business/
    finance/
    compliance/
    ai/
  policies/
    au/
    ca/
    eu/
    nz/
    uk/
    us/
  infra/
    docker/
    terraform/
    kubernetes/
    monitoring/
  docs/
    adr/
    architecture.md
    compliance-model.md
    data-model.md
    engineering-constitution.md
    roadmap.md
    security-privacy-threat-model.md
    standards-and-assumptions.md
```

Do not create all directories until a real module needs them. Empty structure is weaker than tested structure.
