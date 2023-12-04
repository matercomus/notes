# Human-robot interaction
The diagram below represents a typical interaction between a customer and a robot in a grocery store checkout scenario. It outlines the process from the moment the customer approaches the checkout to the completion of the transaction. The diagram includes various paths based on different situations such as successful scanning of items, loyalty card processing, and payment methods. It also incorporates error handling and fallback mechanisms for scenarios like scanning errors and payment failures. The flow ensures a smooth and efficient checkout experience for the customer while effectively managing potential issues.

```mermaid
graph TD
    A[Customer approaches] --> B[Robot greets customer]
    B --> C[Robot starts scanning items]
    C --> D[Robot scans an item]
    D --> E{Item scanned successfully?}
    E -->|Yes| F{More items to scan?}
    F -->|Yes| D
    F -->|No| G[All items scanned]
    E -->|No| H[Robot can't scan item]
    H --> I{Robot asks for manual input}
    I -->|Successful| J[Robot continues scanning]
    J --> D
    I -->|Error| K[Robot calls for human assistance]
    K --> L[Human resolves issue]
    L --> J
    G --> M{Robot asks if customer has loyalty card}
    M -->|Yes| N[Robot processes loyalty card]
    M -->|No| O[Robot skips loyalty card]
    N --> P[Robot provides total]
    O --> P
    P --> Q{Customer makes payment}
    Q -->|Successful| R[End of transaction]
    Q -->|Unsuccessful| S[Robot asks for another payment method]
    S --> T{Customer provides new payment method}
    T -->|Successful| U[End of transaction]
    T -->|Unsuccessful| V[Robot calls for human assistance]
    V --> W[Human resolves issue]
    W --> X[End of transaction]

```
