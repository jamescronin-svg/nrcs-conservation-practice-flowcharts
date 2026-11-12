# Practice 646: Seasonal Water Management for Wildlife
**Source Documents:** NRCS CPS 646 (Nov 2024), FY 2026 Practice Payment Scenarios, and CAPP Narrative/Resource Concern Data

[← Back to Master Index](./README.md)

---

## 1. Decision Flowchart

```mermaid
flowchart TD
    %% Styling matching KS Range/Pasture Examples
    classDef header fill:#833C0C,stroke:#592808,color:#FFFFFF,font-weight:bold
    classDef primary fill:#385723,stroke:#203814,color:#FFFFFF,font-weight:bold
    classDef supporting fill:#70AD47,stroke:#507E32,color:#FFFFFF
    classDef reasoning fill:#FFFF00,stroke:#BF9000,color:#000000
    classDef resource fill:#4472C4,stroke:#2F5597,color:#FFFFFF
    classDef decision fill:#000000,stroke:#000000,color:#FFFFFF
    classDef stop fill:#C00000,stroke:#800000,color:#FFFFFF,font-weight:bold

    Start(["<b>Priority Resource Concerns (CPS 646):</b><br/>Terrestrial &amp; Aquatic Habitat for Wildlife, Waterfowl, Shorebirds, Amphibians &amp; Fish"]):::header
    P646["<b>Primary Practice:</b><br/>Seasonal Water Management for Wildlife (Code 646)"]:::primary

    Start --> P646

    %% Eligibility & Scope Gates (CPS 646)
    Elig1(["Complete State-Approved Habitat Evaluation;<br/>verify reliable water supply &amp; water quality"]):::resource
    Gate_Infra{"Is water control infrastructure<br/>(dikes, structures, pumps) in place<br/>OR planned via separate practices?"}:::decision
    Stop_Infra{{"<b>INFRASTRUCTURE REQUIRED FIRST</b><br/>Plan/install Dike (356), Water Control<br/>Structure (587), or Pumping Plant (533) first"}}:::stop

    Gate_Purpose{"Is primary goal permanent wetland<br/>restoration, livestock water, or wastewater?"}:::decision
    Stop_Purpose{{"<b>OUT OF SCOPE FOR 646</b><br/>Use Wetland Restoration (657), Creation (658),<br/>Watering Facility (614), or Pond (378)"}}:::stop

    P646 --> Elig1 --> Gate_Infra
    Gate_Infra -->|No| Stop_Infra
    Gate_Infra -->|Yes| Gate_Purpose
    Gate_Purpose -->|Yes| Stop_Purpose
    Gate_Purpose -->|No - Seasonal Habitat Inundation| PathSelect

    %% Pathway Selection by CAPP Narrative Code
    PathSelect(["<b>Select Planning Objective & CAPP Narrative Code</b>"]):::resource

    PathSelect --> N_CRP(["<b>Narrative: 00N-CRP-R</b><br/>CRP Re-enrollment: Maintain existing<br/>shallow water development"]):::reasoning
    PathSelect --> N_00(["<b>Narrative: 00N</b><br/>Shallow Water Habitat: Seasonally inundate<br/>lands for wildlife &amp;/or floodplain fish refuge"]):::reasoning

    %% 00N-CRP-R Branch
    N_CRP --> CRP_Note(["Manage hydroperiod &amp; drawdown per CRP contract;<br/>maintain depth gauge &amp; control structures."]):::reasoning

    %% 00N Branch (Scenario Selection)
    N_00 --> Gate_Taxa{"Primary Target Taxa &amp;<br/>Flow Requirement?"}:::decision

    Gate_Taxa -->|"Cropland (e.g., Rice) for Fish:<br/>Continual Pumped Flow + Fish Passage"| Scen7["<b>Scenario 7:</b> Pump Water on Cropland for Fish,<br/>Continual Flow of Water (\$118.26/ac)"]:::primary

    Gate_Taxa -->|"Wildlife / Waterfowl / Shorebirds / Amphibians:<br/>Managed Seasonal Standing Water"| Gate_Source{"Water Delivery Method:<br/>Gravity Capture vs. Mechanical Pump?"}:::decision

    %% Gravity Capture Branch
    Gate_Source -->|"Capture / Divert Water<br/>(No Mechanical Pumping)"| Gate_CapLab{"Site Management &amp;<br/>Labor Intensity?"}:::decision
    Gate_CapLab -->|"High Labor<br/>(Heavy beaver activity / inefficient structures)"| Scen3["<b>Scenario 3:</b> Capture Water, High Labor<br/>Inputs Required (\$53.82/ac)"]:::primary
    Gate_CapLab -->|"Low Labor<br/>(No noticeable beaver activity)"| Scen4["<b>Scenario 4:</b> Capture Water, Low Labor<br/>Inputs Required (\$30.54/ac)"]:::primary

    %% Mechanical Pump Branch
    Gate_Source -->|"Pump Water Onsite<br/>(Mechanical Pumping Required)"| Gate_PumpLab{"Site Management &amp;<br/>Labor Intensity?"}:::decision
    Gate_PumpLab -->|"High Labor<br/>(Heavy beaver activity / inefficient structures)"| Scen5["<b>Scenario 5:</b> Pump Water, High Labor<br/>Inputs Required (\$62.15/ac)"]:::primary
    Gate_PumpLab -->|"Low Labor<br/>(No noticeable beaver activity)"| Scen6["<b>Scenario 6:</b> Pump Water, Low Labor<br/>Inputs Required (\$45.48/ac)"]:::primary

    %% Monitoring & Operation & Maintenance Feedback Loop
    OM(["<b>Monitoring &amp; O&amp;M (CPS 646):</b><br/>Install visible depth gauge; log depth weekly (capture) or<br/>2x/week (pump); monitor temp/DO for fish; execute planned drawdown"]):::resource
    Scen3 & Scen4 & Scen5 & Scen6 & Scen7 -.->|Feedback to Design| OM
    OM -.-> P646

    %% Supporting Practices Fallback for Non-646 Resource Concerns
    Fallback(["<b>Unresolved Spreadsheet Resource Concerns?</b><br/>(Infrastructure Construction, Wetland Vegetation, Invasive Weeds, Erosion)"]):::resource
    P646 --> Fallback

    Fallback --> Supp_Eng["<b>Water Control &amp; Infrastructure (CPS 646):</b><br/>Dike/Levee (356), Structure for Water Control (587),<br/>Pumping Plant (533), Diversion (362), Irrigation Pipeline (430)"]:::supporting
    Fallback --> Supp_Wet["<b>Wetland &amp; Habitat Management (CPS 646):</b><br/>Wetland Wildlife Habitat Mgmt (644), Wetland Restoration (657),<br/>Wetland Creation (658), Wildlife Habitat Planting (420)"]:::supporting
    Fallback --> Supp_Veg["<b>Vegetation, Pest &amp; Access Control (CPS 646):</b><br/>Brush Mgmt (314), Herbaceous Weed Treatment (315),<br/>Prescribed Burning (338), Fence (382), Access Control (472)"]:::supporting
```

---

## 2. Resource Concern & Component Mapping Matrix

| Resource Concern Category (CAPP) | Resource Concern & Components (CAPP) | Direct Match to CPS 646? | Matching Narrative Code & Scenario(s) | Required Supporting Practices (from CPS 646) |
| :--- | :--- | :--- | :--- | :--- |
| **Animals (Terrestrial habitat)** | • Terrestrial habitat for wildlife and invertebrates (waterfowl, shorebirds, wading birds, amphibians, reptiles, mammals) | **Yes (Primary Purpose)** | **00N**:<br>• **Gravity Capture**: Scen. 3 (High Labor), Scen. 4 (Low Labor)<br>• **Mechanical Pump**: Scen. 5 (High Labor), Scen. 6 (Low Labor)<br>**00N-CRP-R**: CRP Maintenance | **Wetland Wildlife Habitat Management (644)**, **Wildlife Habitat Planting (420)**, **Dike/Levee (356)**, **Structure for Water Control (587)**; exclude predatory fish if managing for amphibians. |
| **Animals (Aquatic habitat)** | • Aquatic habitat for fish and other organisms (floodplain/off-channel refuge & rearing)<br>• Water temperature effects on aquatic habitat | **Yes (Primary Purpose)** | **00N**:<br>• **Cropland Fish Habitat**: Scen. 7 (Pump Water on Cropland for Fish, Continual Flow — monitors temp &amp; dissolved oxygen)<br>• **Floodplain Refuge**: Scen. 3 or 4 | **Stream Habitat Improvement &amp; Management (395)**, **Aquatic Organism Passage (396)**, **Structure for Water Control (587)** (modified for fish passage). |
| **Water (Weather resilience)** | • Ponding and flooding<br>• Seasonal high water table &amp; seeps<br>• Naturally available moisture use | **Partial (Hydroperiod Mgmt)** | **00N**: Scen. 3–7 (Active regulation of seasonal inundation depth, timing, and drawdown schedules) | **Structure for Water Control (587)**, **Dike/Levee (356)**, **Diversion (362)**, **Subsurface Drain (606)** (where drainage regulation is needed). |
| **Long term protection of land** | • Loss of wetland functions and values<br>• Loss of floodplain functions and values<br>• Threat of conversion | **Partial (Functional / CRP)** | **00N-CRP-R** (maintains existing shallow water development on CRP)<br>**00N** (restores seasonal floodplain/wetland hydroperiods) | **Wetland Restoration (657)**, **Wetland Creation (658)**, **Wetland Enhancement (659)** (required for permanent wetland restoration/development). |
| **Plants (Degraded plant condition)** & **Plants (Pest pressure)** | • Plant productivity &amp; health, structure &amp; composition<br>• Invasive species &amp; plant pest pressure | **No (Supporting / Drawdown)** | *Timed drawdowns stimulate moist-soil annuals; invasive wetland plants must be controlled via supporting practices*. | **Wetland Wildlife Habitat Management (644)**, **Herbaceous Weed Treatment (315)**, **Brush Management (314)**, **Prescribed Burning (338)**. |
| **Water (Field sediment, nutrient, pathogen, &amp; pesticide loss)** | • Sediment from erosion sources<br>• Nonpoint N, P, pathogen, &amp; pesticide losses | **Indirect Co-Benefit / Caution** | **00N**: Impounded seasonal water settles suspended sediments and retains nutrients prior to scheduled drawdown; *verify water supply is free of harmful pesticides/contaminants*. | **Filter Strip (393)**, **Sediment Basin (350)**, **Pest Management Conservation System (595)**. |
| **Soil (Wind and water erosion)** & **Soil (Concentrated erosion)** | • Sheet, rill, wind, bank, and gully erosion | **No (Infrastructure / Caution)** | *Avoid erosive discharge during drawdown; physical bank/gully stabilization requires structural practices*. | **Grade Stabilization Structure (410)**, **Streambank &amp; Shoreline Protection (580)**, **Critical Area Planting (342)**. |
| **Animals (Livestock production limitation)** | • Inadequate livestock water quantity/quality/distribution<br>• Feed/forage balance &amp; shelter | **No (Exclusion Rule)** | *CPS 646 is not for livestock watering; livestock must be excluded or managed so they do not degrade water quality/habitat*. | **Fence (382)**, **Access Control (472)**, **Watering Facility (614)**, **Prescribed Grazing (528)**. |
