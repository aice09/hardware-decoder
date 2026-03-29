flowchart TD
    A([Start]) --> B[Select Device / System Type]

    B --> B1[Laptop / Mini PC]
    B --> B2[Desktop]
    B --> B3[Workstation]
    B --> B4[Server]
    B --> B5[Legacy Server]
    B --> B6[Unknown / Manual Mode]

    B1 --> C1[Default Form Factor: SODIMM]
    B2 --> C2[Default Form Factor: DIMM]
    B3 --> C3[Default Form Factor: DIMM]
    B4 --> C4[Default Form Factor: DIMM]
    B5 --> C5[Default Form Factor: DIMM]
    B6 --> C6[User manually selects Form Factor]

    C1 --> D1[Allowed Module Types: U, E optional]
    C2 --> D2[Allowed Module Types: U, E optional]
    C3 --> D3[Allowed Module Types: U, E, R optional]
    C4 --> D4[Allowed Module Types: E, R, LR, FB legacy]
    C5 --> D5[Allowed Module Types: FB, R, E]
    C6 --> D6[Allowed Module Types depend on selected Form Factor]

    D1 --> E[Select Form Factor]
    D2 --> E
    D3 --> E
    D4 --> E
    D5 --> E
    D6 --> E

    E --> E1{Form Factor}
    E1 -->|DIMM| F1[DIMM: full-size module]
    E1 -->|SODIMM| F2[SODIMM: laptop / compact module]

    F1 --> G1[DIMM allows: U, E, R, LR, FB legacy]
    F2 --> G2[SODIMM allows: U, E specialized]

    G1 --> H[Select Module Type]
    G2 --> H

    H --> H1{Module Type}
    H1 -->|U| I1[UDIMM / unbuffered<br/>Usually desktop or laptop class]
    H1 -->|E| I2[ECC UDIMM<br/>Entry server / workstation class]
    H1 -->|R| I3[RDIMM / Registered<br/>Server class only]
    H1 -->|LR| I4[LRDIMM / Load-Reduced<br/>Higher-capacity server class]
    H1 -->|FB| I5[FB-DIMM / Fully Buffered<br/>Legacy server class]

    I1 --> J[Select Generation]
    I2 --> J
    I3 --> J
    I4 --> J
    I5 --> J

    J --> J1{Generation}
    J1 -->|PC2| K1[DDR2<br/>Voltage: 1.8V<br/>Speeds: PC2-4200 / 5300 / 6400]
    J1 -->|PC3| K2[DDR3<br/>Voltage: 1.5V<br/>Speeds: PC3-8500 / 10600 / 12800 / 14900]
    J1 -->|PC3L| K3[DDR3L<br/>Voltage: 1.35V<br/>Speeds: PC3L-10600 / 12800]
    J1 -->|PC4| K4[DDR4<br/>Voltage: 1.2V<br/>Speeds: PC4-17000 / 19200 / 21300 / 23400 / 25600]
    J1 -->|PC5| K5[DDR5<br/>Voltage: about 1.1V<br/>Speeds: PC5-38400 / 44800 / 51200]

    K1 --> L[Select Voltage]
    K2 --> L
    K3 --> L
    K4 --> L
    K5 --> L

    L --> M[Select Speed / Bandwidth]
    M --> N[Optional: Select Rank]

    N --> N1{Rank selected?}
    N1 -->|No| O[Proceed without rank]
    N1 -->|Yes| P[Rank options:<br/>1Rx8 / 2Rx8 / 1Rx16 / 2Rx4 / 4Rx4]

    O --> Q[Build Decoded Result]
    P --> Q

    Q --> Q1[Display:<br/>Decoded Label<br/>Generation<br/>Voltage<br/>Speed<br/>Form Factor<br/>Module Type<br/>Rank if selected<br/>Typical Use]
    Q1 --> R[Run Validation / Warning Rules]

    R --> R1{Any invalid or unusual combination?}

    R1 -->|No| S([Show final result])
    R1 -->|Yes| T[Show warnings / notes]

    T --> T1[SODIMM + RDIMM/LRDIMM/FB = invalid]
    T --> T2[Laptop + DIMM = unusual]
    T --> T3[Server + U = uncommon]
    T --> T4[Desktop + RDIMM = usually unsupported]
    T --> T5[FB-DIMM = legacy only]
    T --> T6[Always verify motherboard / CPU / BIOS support]

    T1 --> S
    T2 --> S
    T3 --> S
    T4 --> S
    T5 --> S
    T6 --> S
