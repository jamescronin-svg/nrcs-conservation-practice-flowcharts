# Practice 658: Wetland Creation
**Source Documents:** NRCS CPS 658 (Jan 2026), FY 2026 Practice Payment Scenarios, and CAPP Narrative/Resource Concern Data

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

    Start(["<b>Priority Resource Concerns (CPS 658):</b><br/>Terrestrial &amp; Aquatic Wildlife Habitat, Water Quality &amp; Flood Storage, Wetland Functions"]):::header
    P658["<b>Primary Practice:</b><br/>Wetland Creation (Code 658)"]:::primary

    Start --> P658

    %% Eligibility & Scope Gates (CPS 658)
    Elig1(["Verify site was HISTORICALLY A NON-WETLAND<br/>with adequate water supply &amp; suitable soils/topography"]):::resource
    Gate_Hist{"Was site historically a natural<br/>or degraded wetland?"}:::decision
    Stop_Hist{{"<b>DO NOT USE CODE 658</b><br/>Use Wetland Restoration (657) on former wetlands<br/>or Wetland Enhancement (659) on existing wetlands"}}:::stop

    Gate_Waste{"Is primary purpose ag wastewater treatment<br/>or deep-water livestock/irrigation storage?"}:::decision
    Stop_Waste{{"<b>OUT OF SCOPE FOR 658</b><br/>Use Constructed Wetland (656) for wastewater<br/>or Pond (378) for deep water storage"}}:::stop

    P658 --> Elig1 --> Gate_Hist
    Gate_Hist -->|Yes| Stop_Hist
    Gate_Hist -->|No - Historically Non-Wetland| Gate_Waste
    Gate_Waste -->|Yes| Stop_Waste
    Gate_Waste -->|No - Valid Habitat/Function Creation| PathSelect

    %% Pathway Selection by CAPP Narrative Code
    PathSelect(["<b>Select Program / Objective &amp; CAPP Narrative Code</b>"]):::resource

    PathSelect --> N_CRP(["<b>Narrative: 00N-CRP-R</b><br/>CRP Re-enrollment: Maintain &amp; manage<br/>existing created wetland(s)"]):::reasoning
    PathSelect --> N_00(["<b>Narrative: 00N</b><br/>Creation: Establish wetland hydrology &amp;<br/>hydrophytic vegetation on non-wetland site"]):::reasoning

    %% 00N-CRP-R Branch
    N_CRP --> CRP_Note(["Maintain created wetland embankments, liners,<br/>&amp; vegetative buffers per CRP contract."]):::reasoning

    %% 00N Branch (Scenario Selection)
    N_00 --> Gate_Liner{"Basin Depth &amp; Soil<br/>Water-Holding Capacity?"}:::decision

    Gate_Liner -->|"Shallow Vernal Pool (&lt; 2 ft deep)<br/>Permeable soil requiring liner or compaction"| Scen1["<b>Scenario 1:</b> Vernal Pool Creation<br/>with Liner (\$15.34/cu yd; ~15 sq ft/cu yd)"]:::primary
    Gate_Liner -->|"Seasonal Wetland Excavation<br/>Natural soil holds seasonal hydrology"| Scen3["<b>Scenario 3:</b> Wetland Excavation for<br/>Wildlife (\$5.64/cu yd; spread spoil onsite)"]:::primary

    %% Operation & Maintenance Feedback Loop
    OM(["<b>Operation &amp; Maintenance (CPS 658):</b><br/>Inspect embankments, liners &amp; outlets after storms; prevent<br/>deep-tillage/puncture of clay/synthetic liners; control invasive weeds"]):::resource
    Scen1 & Scen3 -.->|Feedback to Design| OM
    OM -.-> P658

    %% Supporting Practices Fallback for Non-658 Resource Concerns
    Fallback(["<b>Unresolved Spreadsheet Resource Concerns?</b><br/>(Water Control Structures, Seeding/Trees, Upland Buffers, Invasive Weeds, Livestock)"]):::resource
    P658 --> Fallback

    Fallback --> Supp_Eng["<b>Water Control &amp; Embankment Practices (CPS 658):</b><br/>Dike/Levee (356), Structure for Water Control (587),<br/>Diversion (362), Pond Sealing or Lining (520/521), Grade Stab. (410)"]:::supporting
    Fallback --> Supp_Veg["<b>Vegetative &amp; Habitat Management (CPS 658):</b><br/>Wetland Wildlife Habitat Mgmt (644), Wildlife Habitat Planting (420),<br/>Tree/Shrub Estab. (612), Critical Area Planting (342), Conservation Cover (327)"]:::supporting
    Fallback --> Supp_Prot["<b>Upland Buffers, Pest &amp; Livestock Control (CPS 658):</b><br/>Filter Strip (393), Herbaceous Weed Treatment (315),<br/>Brush Mgmt (314), Fence (382), Access Control (472)"]:::supporting
```

---

## 2. Resource Concern & Component Mapping Matrix

| Resource Concern Category (CAPP) | Resource Concern & Components (CAPP) | Direct Match to CPS 658? | Matching Narrative Code & Scenario(s) | Required Supporting Practices (from CPS 658) |
| :--- | :--- | :--- | :--- | :--- |
| **Animals (Terrestrial habitat)** & **Animals (Aquatic habitat)** | • Terrestrial habitat for wildlife and invertebrates (amphibians, waterfowl, shorebirds, pollinators)<br>• Aquatic habitat for fish and other organisms<br>• Water temperature effects on aquatic habitat | **Yes (Primary Purpose)** | **00N**:<br>• **Shallow Vernal Pools (&lt;2 ft)**: Scen. 1 (Vernal Pool Creation with Liner)<br>• **Seasonal Upland Wetland**: Scen. 3 (Wetland Excavation for Wildlife)<br>**00N-CRP-R**: CRP Maintenance | **Wetland Wildlife Habitat Management (644)**, **Seasonal Water Management for Wildlife (646)**, **Wildlife Habitat Planting (420)**, **Structures for Wildlife (649)** (logs/basking platforms). |
| **Long term protection of land** | • Loss of wetland functions and values<br>• Loss of floodplain functions and values<br>• Threat of conversion | **Yes (Primary Purpose)** | **00N**: Scen. 1 or 3 (Creates new wetland functions on capable non-wetland sites)<br>**00N-CRP-R**: Maintains enrolled CRP created wetlands | **Structure for Water Control (587)**, **Dike/Levee (356)**, **Tree/Shrub Establishment (612)** (for forested wetland creation). |
| **Water (Weather resilience)** & **Water (Source water depletion)** | • Ponding and flooding (runoff detention)<br>• Seasonal high water table &amp; seeps<br>• Groundwater &amp; surface water depletion, drought | **Yes (Primary / Hydrology)** | **00N**: Scen. 1 or 3 (Detains surface runoff and creates seasonal water storage; *ensure water rights/supply are adequate*) | **Diversion (362)** (to route clean overland flow into basin), **Grade Stabilization Structure (410)** (at spillway/outlet). |
| **Water (Field sediment, nutrient, pathogen, &amp; pesticide loss)** | • Sediment from erosion sources<br>• Nonpoint N, P, pathogen, &amp; pesticide losses | **Partial (Co-Benefit / Buffer Req.)** | **00N**: Scen. 1 or 3 (Created wetlands filter runoff; *must establish upland vegetated buffers if inflow carries sediment/agrichemicals*) | **Filter Strip (393)**, **Conservation Cover (327)**, **Sediment Basin (350)**; use **Constructed Wetland (656)** if treating concentrated ag wastewater. |
| **Plants (Degraded plant condition)** & **Plants (Pest pressure)** | • Plant productivity &amp; health, structure &amp; composition<br>• Invasive species &amp; plant pest pressure | **Partial (Establishment &amp; O&amp;M)** | **00N**: Establishes native hydrophytic plant communities; *protect liners from deep-rooted woody invasives* | **Wetland Wildlife Habitat Management (644)**, **Herbaceous Weed Treatment (315)**, **Brush Management (314)**, **Prescribed Burning (338)**. |
| **Soil (Wind and water erosion)** & **Soil (Concentrated erosion)** | • Sheet, rill, wind, bank, and gully erosion | **No (Supporting / Earthwork)** | *Excavated spoils spread on adjacent uplands and constructed embankments must be stabilized immediately*. | **Critical Area Planting (342)**, **Mulching (484)**, **Grade Stabilization Structure (410)**. |
| **Animals (Livestock production limitation)** | • Inadequate livestock water, shelter, &amp; forage balance | **No (Exclusion / Protection)** | *CPS 658 is not a livestock watering pond; livestock must be excluded to protect liners, embankments, and water quality*. | **Fence (382)**, **Access Control (472)**, **Watering Facility (614)**, **Pond (378)**. |
| **Soil (Soil quality), Water (Pollutants/Salts), Air (Emissions), Energy** | • Compaction, organic matter, salts, subsidence<br>• Confined animal/mine/agrichemical storage<br>• GHGs, Odor, Ozone, PM, Reactive N, Energy | **No Association** | *No 658 Payment Scenario resolves these components* (present in CSV only due to system-wide RC table cross-join). | Not addressed by CPS 658. Planner must use **Constructed Wetland (656)** for ag wastewater, or dedicated waste/air/energy standards. |
