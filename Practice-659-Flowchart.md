# Practice 659: Wetland Enhancement
**Source Documents:** NRCS CPS 659 (Nov 2024), FY 2026 Practice Payment Scenarios, and CAPP Narrative/Resource Concern Data

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

    Start(["<b>Priority Resource Concerns (CPS 659):</b><br/>Loss of Wetland/Floodplain Functions, Terrestrial &amp; Aquatic Wildlife Habitat, Water Quality &amp; Flood Attenuation"]):::header
    P659["<b>Primary Practice:</b><br/>Wetland Enhancement (Code 659)"]:::primary

    Start --> P659

    %% Eligibility & Scope Gates (CPS 659)
    Elig1(["Verify site is a former, degraded, or naturally functioning wetland<br/>AND assess functional trade-offs before augmenting beyond natural condition"]):::resource
    Gate_Type{"Is site a historically non-wetland OR<br/>for ag wastewater treatment?"}:::decision
    Stop_Type{{"<b>DO NOT USE CODE 659</b><br/>Use Wetland Creation (658) on non-wetlands<br/>or Constructed Wetland (656) for ag wastewater"}}:::stop

    Gate_Goal{"Is goal ONLY restoring historic natural condition<br/>OR annual water/vegetation management?"}:::decision
    Stop_Goal{{"<b>USE RESTORATION OR MANAGEMENT</b><br/>Use Wetland Restoration (657), Seasonal Water<br/>Mgmt (646), or Wetland Wildlife Habitat Mgmt (644)"}}:::stop

    P659 --> Elig1 --> Gate_Type
    Gate_Type -->|Yes| Stop_Type
    Gate_Type -->|No - Existing/Degraded Wetland| Gate_Goal
    Gate_Goal -->|Yes| Stop_Goal
    Gate_Goal -->|No - Augment Beyond Natural Condition| N_00

    %% Single CAPP Narrative Code
    N_00(["<b>CAPP Narrative: 00N</b><br/>Enhancement: Augment wetland functions beyond original natural conditions<br/>to increase capacity of specific targeted wetland functions"]):::reasoning

    N_00 --> Gate_Action{"Primary Hydrologic / Topographic<br/>Enhancement Mechanism?"}:::decision

    %% Tile Daylight Branch
    Gate_Action -->|"Remove Existing Tile Lines &amp;<br/>Create New Surface Outlets"| Scen1["<b>Scenario 1:</b> Daylight Tile Lines<br/>(\$4.45/cu yd; ~3 linear ft/cu yd)"]:::primary

    %% Earthwork / Excavation / Topographic Complexity Branch
    Gate_Action -->|"Earthwork: Enlarge Wetland Footprint,<br/>Add Topographic Complexity, or Fill Ditches"| Gate_Wet{"Site Soil Moisture &amp;<br/>Equipment Requirement?"}:::decision

    %% Dry Soils Branch
    Gate_Wet -->|"Dry Soil Conditions<br/>(Standard Dozer / Excavator)"| Gate_DryHaul{"Spoil Disposal or<br/>Fill Source Location?"}:::decision
    Gate_DryHaul -->|"Onsite Earthwork<br/>(Spread spoil on adjacent upland)"| Scen2["<b>Scenario 2:</b> Earthwork, Dry Soil<br/>Conditions (\$5.63/cu yd)"]:::primary
    Gate_DryHaul -->|"Offsite Haul<br/>(Dispose spoil or haul fill offsite)"| Scen4["<b>Scenario 4:</b> Earthwork Dry Soil,<br/>Offsite (\$7.86/cu yd)"]:::primary

    %% Wet Soils Branch
    Gate_Wet -->|"Wet Soil Conditions<br/>(Low-ground-pressure gear to prevent compaction)"| Gate_WetHaul{"Spoil Disposal or<br/>Fill Source Location?"}:::decision
    Gate_WetHaul -->|"Onsite Earthwork<br/>(Spread spoil on adjacent upland)"| Scen3["<b>Scenario 3:</b> Earthwork, Wet Soil<br/>Conditions (\$6.04/cu yd)"]:::primary
    Gate_WetHaul -->|"Offsite Haul<br/>(Dispose spoil or haul fill offsite)"| Scen5["<b>Scenario 5:</b> Earthwork Wet Soil,<br/>Offsite (\$8.89/cu yd)"]:::primary

    %% Operation & Maintenance Feedback Loop
    OM(["<b>Operation &amp; Maintenance (CPS 659):</b><br/>Inspect embankments, outlets &amp; water control structures after storms;<br/>control invasive wetland species; maintain upland vegetative buffers"]):::resource
    Scen1 & Scen2 & Scen3 & Scen4 & Scen5 -.->|Feedback to Design| OM
    OM -.-> P659

    %% Supporting Practices Fallback for Non-659 Resource Concerns
    Fallback(["<b>Unresolved Spreadsheet Resource Concerns?</b><br/>(Water Control Structures, Seeding/Trees, Invasive Weeds, Sediment Buffers, Livestock)"]):::resource
    P659 --> Fallback

    Fallback --> Supp_Eng["<b>Hydraulic &amp; Structural Practices (CPS 659):</b><br/>Structure for Water Control (587), Dike/Levee (356),<br/>Grade Stabilization Structure (410), Diversion (362), Subsurface Drain (606)"]:::supporting
    Fallback --> Supp_Veg["<b>Vegetative &amp; Habitat Management (CPS 659):</b><br/>Wetland Wildlife Habitat Mgmt (644), Seasonal Water Mgmt (646),<br/>Tree/Shrub Estab. (612), Wildlife Habitat Planting (420), Critical Area (342)"]:::supporting
    Fallback --> Supp_Prot["<b>Buffers, Pest &amp; Livestock Protection (CPS 659):</b><br/>Filter Strip (393), Herbaceous Weed Treatment (315),<br/>Brush Mgmt (314), Fence (382), Access Control (472)"]:::supporting
```

---

## 2. Resource Concern & Component Mapping Matrix

| Resource Concern Category (CAPP) | Resource Concern & Components (CAPP) | Direct Match to CPS 659? | Matching Narrative Code & Scenario(s) | Required Supporting Practices (from CPS 659) |
| :--- | :--- | :--- | :--- | :--- |
| **Long term protection of land** | • Loss of wetland functions and values<br>• Loss of floodplain functions and values<br>• Threat of conversion | **Yes (Primary Purpose)** | **00N**: Scen. 1, 2, 3, 4, 5 (Augments specific wetland functions—flood storage, water quality, or habitat—beyond baseline) | **Structure for Water Control (587)**, **Dike/Levee (356)**, **Wetland Wildlife Habitat Management (644)**. |
| **Animals (Terrestrial habitat)** & **Animals (Aquatic habitat)** | • Terrestrial habitat for wildlife and invertebrates<br>• Aquatic habitat for fish and other organisms<br>• Water temperature effects on aquatic habitat | **Yes (Primary Purpose)** | **00N**:<br>• **Expand Surface Water**: Scen. 1 (Daylight Tile Lines)<br>• **Topographic Complexity / Micro-topography**: Scen. 2, 3, 4, 5 (creates varied water depths for waterfowl, amphibians &amp; fish) | **Wetland Wildlife Habitat Management (644)**, **Seasonal Water Management for Wildlife (646)**, **Structures for Wildlife (649)** (logs/basking structures). |
| **Water (Weather resilience)** & **Water (Source water depletion)** | • Ponding and flooding (increased flood storage)<br>• Seasonal high water table &amp; seeps<br>• Groundwater &amp; surface water depletion, drought | **Yes (Primary Purpose)** | **00N**: Scen. 1–5 (Increases basin detention capacity, hydroperiod duration, and groundwater recharge) | **Diversion (362)**, **Grade Stabilization Structure (410)** (outlet erosion control), **Subsurface Drain (606)** (adjacent drainage protection). |
| **Water (Field sediment, nutrient, pathogen, &amp; pesticide loss)** | • Sediment from erosion sources<br>• Nonpoint N, P, pathogen, &amp; pesticide losses | **Yes (Primary / Co-Benefit)** | **00N**: Scen. 1–5 (Increased residence time &amp; surface area enhance nutrient denitrification and sediment retention; *install buffers if inflow is sediment-laden*) | **Filter Strip (393)**, **Riparian Herbaceous Cover (390)**, **Sediment Basin (350)**. |
| **Plants (Degraded plant condition)** & **Plants (Pest pressure)** | • Plant productivity &amp; health, structure &amp; composition<br>• Invasive species &amp; plant pest pressure | **Partial (Topographic / O&amp;M)** | **00N**: Topographic variation (Scen. 2–5) supports diverse emergent/submergent plant zones; *control invasives stimulated by earthwork* | **Herbaceous Weed Treatment (315)**, **Brush Management (314)**, **Prescribed Burning (338)**, **Tree/Shrub Establishment (612)**. |
| **Soil (Wind and water erosion)** & **Soil (Concentrated erosion)** | • Sheet, rill, wind, bank, and gully erosion | **No (Supporting / Earthwork)** | *Spoil spread on adjacent uplands and modified outlets must be stabilized immediately*. | **Critical Area Planting (342)**, **Mulching (484)**, **Grade Stabilization Structure (410)**. |
| **Animals (Livestock production limitation)** | • Inadequate livestock water, shelter, &amp; forage balance | **No (Exclusion / Managed Grazing)** | *Livestock must be excluded during establishment or managed under prescribed grazing to protect enhanced wetland features*. | **Fence (382)**, **Access Control (472)**, **Prescribed Grazing (528)**, **Watering Facility (614)**. |
| **Soil (Soil quality), Water (Pollutants/Salts), Air (Emissions), Energy** | • Compaction, organic matter, salts, subsidence<br>• Confined animal/mine/agrichemical storage<br>• GHGs, Odor, Ozone, PM, Reactive N, Energy | **No Association** | *No 659 Payment Scenario resolves these components* (present in CSV only due to system-wide RC table cross-join). | Not addressed by CPS 659. Planner must use **Constructed Wetland (656)** for ag wastewater, or dedicated waste/air/energy standards. |
