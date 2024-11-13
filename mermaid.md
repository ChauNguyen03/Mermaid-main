flowchart LR
W[Start]--> A[User selected a store?]
    
    %% No Store Selected
    A -->|No| B{Inventory.Quantity > 0?}
    B -->|Yes| C{filter.store = specific store?}
    B -->|No| L[Display Out-of-Stock]
    C -->|Yes| D[Display Available Online]
    C -->|No| E{filter.store = other specific store?}
    E -->|Yes| F[Display Available Online & In-store]
    E -->|No| G[Display Out-of-Stock]

    %% User Selected a Store
    A -->|Yes| H{Inventory.Quantity > 0?}
    H -->|No| L
    H -->|Yes| I{filter.store = other specific store?}
    I -->|Yes| J[Display Available Online]
    I -->|No| K[Display Available Online & at 'Selected Store Name']

    %% End node
    D --> M[End]
    F --> M
    G --> M
    J --> M
    K --> M
    L --> M

    