## Your final flow is now
```text
DEV GitOps digest
        ↓
verify digest exists in DEV ECR
        ↓
find original sha-* tag
        ↓
check QA ECR
        ↓
same digest already there?
      /       \
    YES        NO
     ↓          ↓
  skip copy   crane copy
      \        /
       ↓      ↓
       verify QA digest
             ↓
       checkout GitOps main
             ↓
       check open PR
        /          \
      YES           NO
       ↓             ↓
      STOP      check branch
                   /    \
                 YES      NO
                  ↓        ↓
               fetch     create
                  \        /
                   ↓      ↓
                 update QA values
                       ↓
                    commit
                       ↓
                     push
                       ↓
                  create PR
                       ↓
                  PR → main
                       ↓
                    merge
                       ↓
                      QA
```
