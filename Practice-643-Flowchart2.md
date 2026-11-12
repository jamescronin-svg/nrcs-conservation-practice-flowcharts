# Practice 643: Restoration of Rare or Declining Natural Communities
**Source Documents:** NRCS CPS 643, FY 2026 Practice Payment Scenarios, and CAPP Narrative/Resource Concern Data

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

    Start(["<b>Priority Resource Concerns (CPS 643):</b><br/>Degraded Plant Condition & Inadequate Wildlife Habitat"]):::header
    P643["<b>Primary Practice:</b><br/>Restoration of Rare or Declining Natural Communities (Code 643)"]:::primary

    Start --> P643

    %% Eligibility Gate
    Elig1(["Site historically supported a rare/declining community<br/>OR local culturally important community"]):::resource
    Gate1{"Can target conditions be met<br/>SOLELY via annual management<br/>(Burn, Graze, FSI, Pest Mgmt)?"}:::decision
    Stop1{{"<b>DO NOT USE CODE 643</b><br/>Use annual management standards<br/>(e.g., 338, 528, 666, 314/315)"}}:::stop

    P643 --> Elig1 --> Gate1
    Gate1 -->|Yes| Stop1
    Gate1 -->|No - Abiotic/Biotic Reestablishment Needed| PathSelect

    %% Pathway Selection by Narrative Code & Ecosystem
    PathSelect(["<b>Select Ecosystem & Narrative Code Pathway</b>"]):::resource

    PathSelect --> N_CRP(["<b>Narrative: 00N-CRP-R</b><br/>CRP Re-enrollment: Maintain existing<br/>rare/declining communities"]):::reasoning
    PathSelect --> N_00(["<b>Narrative: 00N</b><br/>Upland / Terrestrial / Wetland<br/>Abiotic & Biotic Restoration"]):::reasoning
    PathSelect --> N_01(["<b>Narrative: 01N</b><br/>Streams & Floodplains<br/>Low-Tech Process-Based Restoration"]):::reasoning
    PathSelect --> N_02(["<b>Narrative: 02N</b><br/>Coastal / Estuarine<br/>Subtidal Oyster Reef Restoration"]):::reasoning

    %% 00N-CRP-R Branch
    N_CRP --> CRP_Note(["Requires existing CRP cover maintenance.<br/>Check state-specific CRP payment schedules<br/>or associated management practices."]):::reasoning

    %% 00N Branch (Upland / Micro-Topography)
    N_00 --> Gate_Topo{"Is micro-topographic<br/>excavation required?"}:::decision
    Gate_Topo -->|"Shallow (2-6 in)<br/>Farm Equipment"| Scen5["<b>Scenario 5:</b> Development of Shallow<br/>Micro-Topographic Features w/ Normal Farm Equip."]:::primary
    Gate_Topo -->|"Deep (6-12 in)<br/>Heavy Dozer"| Scen6["<b>Scenario 6:</b> Development of Deep<br/>Micro-Topographic Features w/ Heavy Equip."]:::primary

    %% 01N Branch (Streams & Floodplains)
    N_01 --> Gate_Stream{"Structure Material &<br/>Hydrologic Objective?"}:::decision
    Gate_Stream -->|"Woody / Beaver Dam Analogs<br/>(BDAs or PALS)"| Scen221["<b>Scenario 221:</b> Beaver Dam Analogues<br/>or Post-Assisted Log Structures"]:::primary
    Gate_Stream -->|"Rock Structures<br/>(Zuni Bowls, One-Rock Dams)"| Scen226["<b>Scenario 226:</b> Rock Structure"]:::primary

    %% 02N Branch (Oyster Reefs)
    N_02 --> Gate_Oyster{"Oyster Restoration Method<br/>& Natural Recruitment?"}:::decision
    Gate_Oyster -->|"Bagged Dredging +<br/>1M Spat on Shell"| Scen247["<b>Scenario 247:</b> Bagged Dredging,<br/>Spat on Shell"]:::primary
    Gate_Oyster -->|"Barge Crane<br/>(~100 tons shell)"| Scen289["<b>Scenario 289:</b> Barge Crane"]:::primary
    Gate_Oyster -->|"No Nearby Oysters<br/>(Diploid Spat Totes)"| Scen310["<b>Scenario 310:</b> Restoration,<br/>Spat on Shell Only"]:::primary
    Gate_Oyster -->|"Manual Boat Totes<br/>(Clean Shell Only)"| Scen331["<b>Scenario 331:</b> Restoration,<br/>Communities with Shell Only"]:::primary
    Gate_Oyster -->|"Shoreline Reef<br/>(2k-5k bushels/ac)"| Scen352["<b>Scenario 352:</b> Restoration,<br/>Planted Shells on New Site"]:::primary
    Gate_Oyster -->|"Tidal River Bottom<br/>(Base + Acre-Inch)"| Scen436["<b>With Spat:</b> Scen. 436 (Base) + 457 (Impl.)<br/><b>No Spat:</b> Scen. 478 (Base) + 499 (Impl.)"]:::primary

    %% Monitoring Feedback Loop
    Mon(["<b>Post-Restoration Monitoring (O&M):</b><br/>Scen. 373 (Yr 1), Scen. 394 (Yr 2), Scen. 415 (Yr 3)"]):::primary
    Scen247 & Scen289 & Scen310 & Scen331 & Scen352 & Scen436 -.->|Feedback to Design| Mon
    Mon -.-> P643

    %% Supporting Practices Fallback for Non-643 Resource Concerns
    Fallback(["<b>Unresolved Spreadsheet Resource Concerns?</b><br/>(Erosion, Heavy Hydrology, Invasive Pests, Fire, Ag/Livestock)"]):::resource
    P643 --> Fallback

    Fallback --> Supp_Eng["<b>Heavy Engineering & Hydrology (CPS 643):</b><br/>Dike (356), Diversion (362), Pond (378), Grade Stab. (410),<br/>Streambank Prot. (580), Open Channel (582),<br/>Channel Bed Stab. (584), Water Control Struct. (587)"]:::supporting
    Fallback --> Supp_Veg["<b>Facilitating Vegetative & Disturbance (CPS 643):</b><br/>Prescribed Burning (338), Forest Stand Imp. (666),<br/>Integrated Pest Mgmt (595), Nurse Crop / Mycorrhiza"]:::supporting
```

---

## 2. Resource Concern & Component Mapping Matrix

| Resource Concern Category (CAPP) | Resource Concern & Components (CAPP) | Direct Match to CPS 643? | Matching Narrative Code & Scenario(s) | Required Supporting Practices (from CPS 643) |
| :--- | :--- | :--- | :--- | :--- |
| **Plants (Degraded plant condition)** | • Plant productivity and health<br>• Plant structure and composition | **Yes (Primary Purpose)** | **00N**: Scen. 5 (Shallow Micro-Topo), Scen. 6 (Deep Micro-Topo)<br>**01N**: Scen. 221 (BDAs/PALS), Scen. 226 (Rock)<br>**00N-CRP-R**: CRP Maintenance | Facilitating practices per CPS 643: Prescribed Burning, Forest Stand Improvement, local genotype seeding, nurse crops. |
| **Animals (Terrestrial habitat)** | • Terrestrial habitat for wildlife and invertebrates | **Yes (Primary Purpose)** | **00N**: Scen. 5 (6'x6' depressions/mounds), Scen. 6 (10'x10' depressions/mounds)<br>**01N**: Scen. 221, Scen. 226 | Stage restoration or conserve adjacent refugia habitat for disturbance-intolerant wildlife. |
| **Animals (Aquatic habitat)** | • Aquatic habitat for fish and other organisms<br>• Water temperature effects on aquatic habitat | **Yes (Primary Purpose)** | **01N (Streams)**: Scen. 221 (BDAs/PALS)<br>**02N (Estuaries)**: Scen. 247, 289, 310, 331, 352, 436/457, 478/499<br>**Monitoring**: Scen. 373, 394, 415 | **Open Channel (582)**, **Channel Bed Stabilization (584)**, **Structure for Water Control (587)**. |
| **Soil (Concentrated erosion)** & **Soil (Wind and water erosion)** | • Bank erosion from streams/shorelines<br>• Classic & ephemeral gully erosion<br>• Sheet, rill, and wind erosion | **Partial (Secondary)** | **01N (Gullies/Channels)**: Scen. 226 (Rock Structure / Zuni bowls for head-cutting), Scen. 221 (BDAs)<br>**00N (Sheet/Rill)**: Scen. 5 & 6 (reduces runoff) | **Grade Stabilization Structure (410)**, **Streambank & Shoreline Protection (580)**, **Diversion (362)**. |
| **Water (Weather resilience)** & **Water (Source water depletion)** | • Ponding and flooding<br>• Seasonal high water table & seeps<br>• Drought susceptibility & moisture mgmt<br>• Surface/groundwater depletion, drifted snow | **Partial (Abiotic Hydrology)** | **00N**: Scen. 5 & 6 (increases water infiltration, creates short-duration ponding <7 days)<br>**01N**: Scen. 221 (raises water tables, reconnects floodplains) | **Dike (356)**, **Diversion (362)**, **Pond (378)**, **Structure for Water Control (587)**. |
| **Soil (Soil quality limitations)** | • Aggregate instability & compaction<br>• Organic matter depletion & subsidence<br>• Concentration of salts/chemicals<br>• Soil organism habitat loss | **Partial (Abiotic Soil)** | **00N**: Scen. 5 & 6 (plowing/loosening compacted soil; depressions trap organic matter/nutrients) | Restore soil texture/chemistry (pH, salinity, fertility); inoculate **soil mycorrhiza**; use **nurse crops**. |
| **Plants (Pest pressure)** | • Invasive species<br>• Plant pest pressure<br>• Chemical resistance | **No (Supporting Only)** | *Cannot use 643 if pest management alone solves the issue*. | **Integrated Pest Management (IPM)** (CPS 643 Considerations); weed/invasive removal prior to planting. |
| **Plants (Fire management)** | • Wildfire hazard from biomass accumulation | **No (Supporting Only)** | *Cannot use 643 if prescribed burning alone solves the issue*. | **Prescribed Burning** (CPS 643 Facilitating Practices). |
| **Water (Field sediment, nutrient, pathogen, pesticide, & salt loss)** | • Sediment from erosion sources<br>• Nonpoint N, P, pathogen, pesticide, & salt losses | **Indirect Co-Benefit** | **00N**: Scen. 5 & 6 (depressions capture sediment/nutrients)<br>**02N**: All Oyster Scenarios (bivalve filtration removes nutrients/sediment) | **Diversion (362)**, **Nurse Crops** (to reduce residual pesticides and excess fertility). |
| **Long term protection of land** | • Threat of conversion (ag/grassland)<br>• Loss of floodplain, forestland, or wetland functions | **Indirect / Administrative** | **00N-CRP-R** (maintains enrolled CRP land)<br>**01N** (restores floodplain functions)<br>**00N** (Scen. 6 pre-wetland restoration) | Requires easement/program enrollment outside CPS 643; pair with wetland/forestland standards. |
