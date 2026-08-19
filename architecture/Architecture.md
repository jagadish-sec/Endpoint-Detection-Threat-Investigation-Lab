```mermaid
%%{
init: {
  "theme": "base",
  "flowchart": {
    "curve": "basis",
    "nodeSpacing": 45,
    "rankSpacing": 70
  },
  "themeVariables": {
    "background":"#0d1117",
    "primaryColor":"#1f2937",
    "primaryBorderColor":"#58a6ff",
    "primaryTextColor":"#ffffff",
    "lineColor":"#00d4ff",
    "fontFamily":"Inter, Segoe UI, Arial",
    "clusterBkg":"#161b22",
    "clusterBorder":"#3b82f6",
    "clusterTextColor":"#ffffff"
  }
}
%%

flowchart TD

    A(("🌍<br>Internet")):::internet
    B["Tor Network<br><b>Scenario 01</b>"]:::external
    C["🛡️ Parrot Security OS VM<br>Attack Simulation"]:::attacker

    D{{NAT / Host-Only<br>Network}}:::network

    subgraph EM["🖥️ Endpoint Monitoring"]
        direction TB

        E["Windows 11 VM<br>Monitored Endpoint"]:::monitor

        F1[(Windows Event Logs)]:::log
        F2[(Sysmon)]:::log
        F3[(Wireshark)]:::log

        G["Wazuh Agent"]:::agent

        E --> F1
        E --> F2
        E --> F3

        F1 --> G
        F2 --> G
        F3 --> G
    end

    subgraph SA["📊 SIEM & Analysis"]
        direction TB

        H["Wazuh Manager"]:::siem

        I1["Rules"]:::analysis
        I2["Threat Hunts"]:::analysis
        I3["Dashboards"]:::analysis

        H --> I1
        H --> I2
        H --> I3
    end

    A --> B
    B --> C
    C --> D
    D --> E
    G --> H

    %% ---------- Classes ----------

    classDef internet fill:#6f42c1,stroke:#c297ff,stroke-width:3px,color:#fff;

    classDef external fill:#2d3748,stroke:#7dd3fc,stroke-width:2px,color:#fff;

    classDef attacker fill:#7f1d1d,stroke:#ff6b6b,stroke-width:3px,color:#fff;

    classDef network fill:#78350f,stroke:#fbbf24,stroke-width:3px,color:#fff;

    classDef monitor fill:#0c4a6e,stroke:#38bdf8,stroke-width:2px,color:#fff;

    classDef log fill:#164e63,stroke:#67e8f9,stroke-width:2px,color:#fff;

    classDef agent fill:#155e75,stroke:#22d3ee,stroke-width:3px,color:#fff;

    classDef siem fill:#14532d,stroke:#4ade80,stroke-width:3px,color:#fff;

    classDef analysis fill:#166534,stroke:#86efac,stroke-width:2px,color:#fff;

    %% ---------- Cluster Styling ----------

    style EM fill:#111827,stroke:#38bdf8,stroke-width:2px,stroke-dasharray:8 5
    style SA fill:#111827,stroke:#4ade80,stroke-width:2px,stroke-dasharray:8 5

    %% ---------- Colored Arrows ----------

    linkStyle default stroke:#00E5FF,stroke-width:3px
```
