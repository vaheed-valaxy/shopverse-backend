## Promortion Flow DEV -> QA 
```text
Job 1
  ↓
Read DEV digest from GitOps
  ↓
Validate sha256 digest
  ↓
Verify digest exists in DEV ECR
  ↓
Find original sha-* tag
  ↓
Check QA ECR
  ├── same digest already exists → Job 2 skipped
  └── image missing              → Job 2 runs
                                      ↓
                                  crane copy
                                      ↓
                                  verify digest
  ↓
Job 3
  ↓
Create digest-based promotion branch
  ↓
Check existing PR
  ↓
Create/reuse branch
  ↓
Update QA values
  ↓
Check diff
  ↓
Commit full digest
  ↓
Push branch
  ↓
Create one PR
```
