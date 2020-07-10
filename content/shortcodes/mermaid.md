---
title: "Mermaid"
date: 2020-07-10T09:53:39-04:00
draft: false
---
(Just taken from the DocDock documentation.)

{{<mermaid align="left">}}
graph LR;
    A[Hard edge] -->|Link text| B(Round edge)
    B --> C{Decision}
    C -->|One| D[Result one]
    C -->|Two| E[Result two]
{{< /mermaid >}}

{{<mermaid align="left">}}
graph LR;
    X --> Y
    linkStyle 0 stroke:#f00,stroke-width:4px;
    Y --> Z
    Z --> X
    linkStyle 1,2 interpolate basis stroke:#0f0,stroke-width:2px;
    X --> A1
    subgraph right
        A2 --> B2
        B2 --> C2
    end
    subgraph left
        A1 --> B1
        B1 --> C1
    end
    C1 --> X
    Z --> A2
    C2 --> Z

    style Y fill:#f9f,stroke:#333,stroke-width:4px

    classDef left fill:#ccf,stroke:#f66,stroke-width:2px,stroke-dasharray: 5, 5
    class A1,B1,C1 left
{{< /mermaid >}}