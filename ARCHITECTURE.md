# Automation Architecture

This diagram shows how the local UI automation flow works without publishing private implementation code.

## Execution Flow

```mermaid
flowchart LR
    A[PowerShell Runner] --> B[Start Local Frontend]
    B --> C[Wait For Base URL]
    C --> D[Maven Test Command]
    D --> E[JUnit 5 Test Suite]
    E --> F[Base UI Test Setup]
    F --> G[Selenium WebDriver]
    G --> H[Page Objects]
    H --> I[Reusable UI Actions]
    I --> J[Assertions]
    J --> K{Test Failed?}
    K -- Yes --> L[Capture Screenshot]
    K -- No --> M[Close Browser]
    L --> M
    M --> N[Stop Frontend]
```

## Framework Layers

```mermaid
flowchart TB
    T[Test Classes] --> P[Page Objects]
    P --> U[UI Actions Helper]
    T --> B[Base Test Setup]
    B --> W[Selenium WebDriver]
    U --> W
    T --> S[Screenshot Extension]
```

## Coverage Model

```mermaid
mindmap
  root((UI Regression))
    Public Routes
      Home
      Marketplace
      Mobile View
    Authentication
      Login Form
      Registration Form
      Role Intent
      Redirect Preservation
    Guest Access
      Address Prompt
      Public Navigation
    Marketplace
      Keyword Search
      Shortcut
      Verified Filter
      Price Sort
      Clear Filters
    Localization
      Hindi Selector
```

## Why This Matters

- The runner makes local execution possible without deployment.
- Page objects keep tests readable and easier to maintain.
- Shared UI actions reduce repeated Selenium code.
- Screenshot capture supports failure analysis.
- The public repository explains the framework without exposing private code.
