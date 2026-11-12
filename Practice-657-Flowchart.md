# Practice 657: Wetland Restoration
**Source Documents:** NRCS CPS 657 (Nov 2024), FY 2026 Practice Payment Scenarios, and CAPP Narrative/Resource Concern Data

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

    Start(["<b>Priority Resource Concerns (CPS 657):</b><br/>Loss of Wetland/Floodplain Functions, Terrestrial &amp; Aquatic Wildlife Habitat, Water Quality &amp; Flood Storage, Carbon Stock / Subsidence"]):::header
    P657["<b>Primary Practice:</b><br/>Wetland Restoration (Code 657)"]:::primary

    Start --> P657

    %% Eligibility & Scope Gates (CPS 657)
    Elig1(["Verify site was historically a natural wetland (hydric soils/geomorphology)<br/>with degraded hydrology, soils, or native plant community"]):::resource
    Gate_Hist{"Was site historically a natural<br/>degraded/drained wetland?"}:::decision
    Stop_Hist{{"<b>DO NOT USE CODE 657</b><br/>Use Wetland Creation (658) on non-wetlands,<br/>Enhancement (659), or Constructed Wetland (656)"}}:::stop

    Gate_Mgmt{"Is ONLY annual water management or<br/>vegetation management needed?"}:::decision
    Stop_Mgmt{{"<b>NO ABIOTIC RESTORATION NEEDED</b><br/>Use Seasonal Water Mgmt (646) or<br/>Wetland Wildlife Habitat Mgmt (644)"}}:::stop

    P657 --> Elig1 --> Gate_Hist
    Gate_Hist -->|No| Stop_Hist
    Gate_Hist -->|Yes| Gate_Mgmt
    Gate_Mgmt -->|Yes| Stop_Mgmt
    Gate_Mgmt -->|No - Hydrologic/Soil Restoration Needed| PathSelect

    %% Pathway Selection by CAPP Narrative Code
    PathSelect(["<b>Select Soil Type / Program &amp; CAPP Narrative Code</b>"]):::resource

    PathSelect --> N_CRP(["<b>Narrative: 00N-CRP-R</b><br/>CRP Re-enrollment: Maintain &amp; manage<br/>existing natural wetland(s)"]):::reasoning
    PathSelect --> N_00(["<b>Narrative: 00N</b><br/>Standard Restoration: Restore abiotic<br/>hydrology/soils on degraded wetland"]):::reasoning
    PathSelect --> N_01(["<b>Narrative: 01N</b><br/>Organic Soil Restoration: Restore hydrology<br/>on drained temperate or boreal histosols"]):::reasoning

    %% 00N-CRP-R Branch
    N_CRP --> CRP_Note(["Maintain restored wetland hydrology &amp; buffers<br/>per CRP contract; control invasive species."]):::reasoning

    %% Scenario Selection Logic for 00N and 01N
    N_00 & N_01 --> Gate_Action{"Primary Hydrologic Restoration Mechanism?"}:::decision

    %% Tile Break Branch
    Gate_Action -->|"Disable Subsurface Tile Drain System<br/>(Remove tile sections, compact, cap ends)"| Scen4["<b>Scenario 4:</b> Tile Break<br/>(\$4.79/cu yd)"]:::primary

    %% Earthwork / Sediment / Ditch Plug Branch
    Gate_Action -->|"Earthwork: Breaching Levees, Ditch Plugs,<br/>Sediment Removal, or Basin Reshaping"| Gate_Wet{"Site Soil Moisture &amp;<br/>Equipment Requirement?"}:::decision

    %% Dry Soils Branch
    Gate_Wet -->|"Dry Soil Conditions<br/>(Standard Dozer / Excavator)"| Gate_DryHaul{"Spoil Disposal or<br/>Fill Source Location?"}:::decision
    Gate_DryHaul -->|"Onsite Earthwork<br/>(Spread/salvage spoil onsite)"| Scen2["<b>Scenario 2:</b> Sediment Removal/Ditch Plugs/Fill,<br/>Dry Soil Conditions (\$5.63/cu yd)"]:::primary
    Gate_DryHaul -->|"Offsite Haul<br/>(Dispose spoil or haul fill offsite)"| Scen1["<b>Scenario 1:</b> Dry Sediment Removal,<br/>Offsite (\$7.86/cu yd)"]:::primary

    %% Saturated / Wet Soils Branch (including Histosols)
    Gate_Wet -->|"Saturated / Wet Soils (or Histosols)<br/>(Low-ground-pressure equipment needed)"| Gate_WetHaul{"Spoil Disposal or<br/>Fill Source Location?"}:::decision
    Gate_WetHaul -->|"Onsite Earthwork<br/>(Move spoil to adjacent upland/fill onsite)"| Scen3["<b>Scenario 3:</b> Sediment Removal/Ditch Plugs/Fill,<br/>Saturated Soils (\$6.04/cu yd)"]:::primary
    Gate_WetHaul -->|"Offsite Haul<br/>(Transport spoil or haul fill offsite)"| Scen5["<b>Scenario 5:</b> Wet Sediment Removal,<br/>Offsite (\$9.41/cu yd)"]:::primary

    %% Operation & Maintenance Feedback Loop
    OM(["<b>Operation &amp; Maintenance (CPS 657):</b><br/>Inspect dikes, ditch plugs &amp; water control structures after major storms;<br/>control invasive wetland plants; maintain upland vegetative buffers"]):::resource
    Scen4 & Scen2 & Scen1 & Scen3 & Scen5 -.->|Feedback to Design| OM
    OM -.-> P657

    %% Supporting Practices Fallback for Non-657 Resource Concerns
    Fallback(["<b>Unresolved Spreadsheet Resource Concerns?</b><br/>(Structures/Dikes, Seeding/Trees, Invasive Weeds, Sediment Buffers, Livestock)"]):::resource
    P657 --> Fallback

    Fallback --> Supp_Eng["<b>Hydraulic &amp; Structural Practices (CPS 657):</b><br/>Structure for Water Control (587), Dike/Levee (356),<br/>Grade Stabilization Structure (410), Diversion (362), Subsurface Drain (606)"]:::supporting
    Fallback --> Supp_Veg["<b>Vegetative &amp; Pest Management (CPS 657):</b><br/>Wetland Wildlife Habitat Mgmt (644), Tree/Shrub Estab. (612),<br/>Conservation Cover (327), Herbaceous Weed Treatment (315), Brush Mgmt (314)"]:::supporting
    Fallback --> Supp_Buf["<b>Upland Buffers &amp; Livestock Protection (CPS 657):</b><br/>Filter Strip (393), Riparian Herbaceous Cover (390),<br/>Fence (382), Access Control (472), Prescribed Grazing (528)"]:::supporting
```

---

## 2. Resource Concern & Component Mapping Matrix

| Resource Concern Category (CAPP) | Resource Concern & Components (CAPP) | Direct Match to CPS 657? | Matching Narrative Code & Scenario(s) | Required Supporting Practices (from CPS 657) |
| :--- | :--- | :--- | :--- | :--- |
| **Long term protection of land** | • Loss of wetland functions and values<br>• Loss of floodplain functions and values<br>• Threat of conversion | **Yes (Primary Purpose)** | **00N**: Scen. 1, 2, 3, 4, 5 (Restores historic wetland hydrology, soils, and floodplain connectivity)<br>**01N**: Scen. 3, 4, 5 (Histosol restoration)<br>**00N-CRP-R**: CRP Maintenance | **Structure for Water Control (587)**, **Dike/Levee (356)**, **Wetland Wildlife Habitat Management (644)**; pair with wetland easements where applicable. |
| **Animals (Terrestrial habitat)** & **Animals (Aquatic habitat)** | • Terrestrial habitat for wildlife and invertebrates<br>• Aquatic habitat for fish and other organisms<br>• Water temperature effects on aquatic habitat | **Yes (Primary Purpose)** | **00N / 01N**: Scen. 1–5 (Re-establishes natural hydroperiods for waterfowl, amphibians, invertebrates, and floodplain fish) | **Wetland Wildlife Habitat Management (644)**, **Seasonal Water Management for Wildlife (646)**, **Tree/Shrub Establishment (612)** (for forested wetlands). |
| **Water (Weather resilience)** & **Water (Source water depletion)** | • Ponding and flooding (floodwater attenuation)<br>• Seasonal high water table &amp; seeps<br>• Groundwater &amp; surface water depletion, drought | **Yes (Primary Purpose)** | **00N / 01N**: Scen. 1–5 (Ditch plugs, levee breaches, and tile breaks restore natural water storage and groundwater recharge) | **Diversion (362)**, **Grade Stabilization Structure (410)** (at outlets to prevent head-cutting), **Subsurface Drain (606)** (to protect adjacent land). |
| **Soil (Soil quality limitations)** & **Air (Air quality emissions)** | • Subsidence (organic soil oxidation)<br>• Organic matter depletion &amp; compaction<br>• GHGs - carbon stock &amp; nitrogen fertilizer | **Yes (Primary Purpose — Histosols)** | **01N**: Scen. 3, 4, 5 (Re-wetting drained temperate/boreal histosols halts peat subsidence and restores carbon sequestration)<br>**00N**: Scen. 1–5 (Low-ground-pressure gear prevents compaction) | **Conservation Cover (327)**, **Critical Area Planting (342)** (stabilize disturbed spoil/dikes immediately). |
| **Water (Field sediment, nutrient, pathogen, &amp; pesticide loss)** | • Sediment from erosion sources<br>• Nonpoint N, P, pathogen, &amp; pesticide losses | **Yes (Primary / Co-Benefit)** | **00N / 01N**: Scen. 1–5 (Restored wetlands trap sediment and denitrify/filter runoff; *install upland buffers if inflow is sediment-laden*) | **Filter Strip (393)**, **Riparian Herbaceous Cover (390)**, **Sediment Basin (350)** (to prevent premature wetland sedimentation). |
| **Plants (Degraded plant condition)** | • Plant productivity and health<br>• Plant structure and composition | **Partial (Hydrologic Foundation)** | **00N / 01N**: Restored hydroperiod enables hydrophytic native plant regeneration; supplemental planting used if seed bank is depleted | **Tree/Shrub Establishment (612)**, **Wildlife Habitat Planting (420)**, **Wetland Wildlife Habitat Management (644)**. |
| **Plants (Pest pressure)** | • Invasive species<br>• Plant pest pressure &amp; chemical resistance | **No (Supporting / O&amp;M)** | *Disturbed wetland soils are vulnerable to reed canarygrass, cattail, or phragmites invasion during restoration*. | **Herbaceous Weed Treatment (315)**, **Brush Management (314)**, **Prescribed Burning (338)**, **Pest Management (595)**. |
| **Soil (Wind and water erosion)** & **Soil (Concentrated erosion)** | • Sheet, rill, wind, bank, and gully erosion | **No (Supporting / Outlet Protection)** | *Earthwork spoils and wetland outlets must be stabilized to prevent erosion*. | **Grade Stabilization Structure (410)**, **Critical Area Planting (342)**, **Mulching (484)**, **Streambank Protection (580)**. |
