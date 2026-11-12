# Practice 420: Wildlife Habitat Planting
**Source Documents:** NRCS CPS 420 (Oct 2018), FY 2026 Practice Payment Scenarios, and CAPP Narrative/Resource Concern Data

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

    Start(["<b>Priority Resource Concerns (CPS 420):</b><br/>Terrestrial Habitat for Wildlife & Invertebrates (Pollinators), Degraded Plant Condition"]):::header
    P420["<b>Primary Practice:</b><br/>Wildlife Habitat Planting (Code 420)"]:::primary

    Start --> P420

    %% Eligibility & Site Assessment Gates (CPS 420)
    Elig1(["State-approved habitat evaluation (WHEG) shows habitat below<br/>planning criteria (&lt; 0.50 of habitat potential)"]):::resource
    Gate_Mgmt{"Can target habitat be met SOLELY<br/>via vegetative management<br/>(Burn, Graze, FSI, Weed Mgmt)?"}:::decision
    Stop_Mgmt{{"<b>DO NOT USE CODE 420</b><br/>Use management practices instead<br/>(e.g., 338, 528, 666, 314/315, 647)"}}:::stop

    Gate_Scope{"Is primary goal tree establishment,<br/>commercial forage, or erosion control?"}:::decision
    Stop_Scope{{"<b>OUT OF SCOPE FOR 420</b><br/>Use Tree Estab. (612), Forage/Range (512/550),<br/>or Critical Area Planting (342)"}}:::stop

    P420 --> Elig1 --> Gate_Mgmt
    Gate_Mgmt -->|Yes| Stop_Mgmt
    Gate_Mgmt -->|No - Planting Required| Gate_Scope
    Gate_Scope -->|Yes| Stop_Scope
    Gate_Scope -->|No - Herbaceous/Shrub Habitat| PathSelect

    %% Pathway Selection by Narrative Code
    PathSelect(["<b>Select Site Objective & CAPP Narrative Code</b>"]):::resource

    PathSelect --> N_CRP(["<b>Narrative: 00N-CRP-R</b><br/>CRP Re-enrollment: Maintain existing<br/>wildlife habitat planting"]):::reasoning
    PathSelect --> N_00(["<b>Narrative: 00N</b><br/>Full Habitat Establishment: Plant herbaceous<br/>or shrub cover to meet &ge; 50% potential"]):::reasoning
    PathSelect --> N_01(["<b>Narrative: 01N</b><br/>Habitat Augmentation: Interplant into<br/>existing habitat for missing life-need"]):::reasoning

    %% 00N-CRP-R Branch
    N_CRP --> CRP_Note(["Manage existing cover per CRP contract.<br/>Schedule disturbance outside primary<br/>nesting/brood-rearing season."]):::reasoning

    %% 01N Branch (Augmenting / Interplanting)
    N_01 --> Gate_01N{"Scale & Planting Method<br/>for Interplanting?"}:::decision
    Gate_01N -->|"Spot Treatment & Hand Planting<br/>(Typ. 225 sq ft; e.g., milkweed/shrubs)"| Scen257["<b>Scenario 257:</b> Interplanting with<br/>Potted Plants or Shrubs ($3.35/sq ft)"]:::primary
    Gate_01N -->|"Acreage-Scale Interplanting<br/>on Cropland (Foregone Income)"| Scen271["<b>Scenario 271:</b> High Species Diversity<br/>on Cropland, Foregone Income ($1,595.98/ac)"]:::primary

    %% 00N Branch (Full Establishment)
    N_00 --> Gate_Scale{"Planting Scale &<br/>Plant Material Type?"}:::decision

    Gate_Scale -->|"Very Small Area (~1/4 ac / 10,890 sq ft)<br/>Potted Plants / Seedlings"| Scen192["<b>Scenario 192:</b> Planting with<br/>Seedlings ($0.77/sq ft)"]:::primary
    Gate_Scale -->|"Small Area (~1/4 ac / 10,890 sq ft)<br/>Herbaceous Plugs"| Scen303["<b>Scenario 303:</b> Planting with<br/>Plugs ($1.35/sq ft)"]:::primary
    Gate_Scale -->|"Small Acreage (&lt; 5 ac)<br/>Combined Seeding + Plugs/Shrubs"| Scen272["<b>Scenario 272:</b> Specialized Seeding<br/>and Plugging ($8,514.32/ac)"]:::primary
    Gate_Scale -->|"Field Scale (Typ. 5 ac)<br/>Broadcast / Drill Seeding"| Gate_Land{"Current Land Use:<br/>Active Cropland vs. Non-Cropland?"}:::decision

    %% Field Scale Cropland vs Non-Cropland
    Gate_Land -->|"Cropland in Production<br/>(Includes Foregone Income)"| Gate_CropDiv{"Species Diversity /<br/>Habitat Requirement?"}:::decision
    Gate_CropDiv -->|Low Diversity| Scen302["<b>Scenario 302:</b> Low Species Diversity<br/>on Cropland, Foregone Income ($1,012.70/ac)"]:::primary
    Gate_CropDiv -->|High Diversity| Scen271
    Gate_CropDiv -->|Specialized Habitat| Scen193["<b>Scenario 193:</b> Specialized Habitat Req.<br/>on Cropland, Foregone Income ($2,362.73/ac)"]:::primary

    Gate_Land -->|"Fallow / Non-Cropland<br/>(No Foregone Income)"| Gate_NonCropDiv{"Species Diversity /<br/>Habitat Requirement?"}:::decision
    Gate_NonCropDiv -->|Low Diversity| Scen301["<b>Scenario 301:</b> Low Species Diversity<br/>on Non-Cropland ($406.91/ac)"]:::primary
    Gate_NonCropDiv -->|High Diversity| Scen299["<b>Scenario 299:</b> High Species Diversity on<br/>Fallow or Non-Cropland ($885.06/ac)"]:::primary
    Gate_NonCropDiv -->|Specialized Habitat| Scen300["<b>Scenario 300:</b> Specialized Habitat Req.<br/>on Non-Cropland ($1,862.08/ac)"]:::primary

    %% Operation & Maintenance Feedback Loop
    OM(["<b>Operation & Maintenance (O&M):</b><br/>Protect from grazing/mowing during establishment;<br/>manage disturbance outside nesting season"]):::resource
    Scen192 & Scen303 & Scen272 & Scen257 & Scen302 & Scen271 & Scen193 & Scen301 & Scen299 & Scen300 -.->|Feedback to Design| OM
    OM -.-> P420

    %% Supporting Practices Fallback for Non-420 Resource Concerns
    Fallback(["<b>Unresolved Spreadsheet Resource Concerns?</b><br/>(Site Prep/Weeds, Livestock Exclusion, Erosion, Fire/Management)"]):::resource
    P420 --> Fallback

    Fallback --> Supp_Prep["<b>Site Prep & Invasive Control (CPS 420):</b><br/>Brush Mgmt (314), Herbaceous Weed Treatment (315),<br/>Pest Mgmt Conservation System (595), Conservation Cover (327)"]:::supporting
    Fallback --> Supp_Mgmt["<b>Protection & Long-Term Mgmt (CPS 420):</b><br/>Fence (382), Access Control (472), Prescribed Burning (338),<br/>Firebreak (394), Prescribed Grazing (528), Early Successional Habitat (647)"]:::supporting
    Fallback --> Supp_Ero["<b>Adjunct Structural / Buffer Practices:</b><br/>Critical Area Planting (342), Filter Strip (393),<br/>Field Border (386), Hedgerow Planting (422), Tree/Shrub Estab. (612)"]:::supporting
```

---

## 2. Resource Concern & Component Mapping Matrix

| Resource Concern Category (CAPP) | Resource Concern & Components (CAPP) | Direct Match to CPS 420? | Matching Narrative Code & Scenario(s) | Required Supporting Practices (from CPS 420) |
| :--- | :--- | :--- | :--- | :--- |
| **Animals (Terrestrial habitat)** | • Terrestrial habitat for wildlife and invertebrates (including pollinators & monarch butterfly) | **Yes (Primary Purpose)** | **00N**: Scen. 192, 193, 271, 272, 299, 300, 301, 302, 303<br>**01N**: Scen. 257 (Interplanting), Scen. 271<br>**00N-CRP-R**: CRP Maintenance | **Field Border (386)**, **Hedgerow Planting (422)**, **Early Successional Habitat Development (647)**, **Tree/Shrub Establishment (612)**. |
| **Plants (Degraded plant condition)** | • Plant productivity and health<br>• Plant structure and composition | **Yes (Primary Purpose)** | **00N**: Scen. 271, 299 (High Diversity), Scen. 193, 300 (Specialized), Scen. 272 (Seed + Plugs)<br>**01N**: Scen. 257, 271 (Augmenting diversity/structure) | **Prescribed Burning (338)**, **Prescribed Grazing (528)** (post-establishment), **Range Planting (550)**. |
| **Soil (Wind and water erosion)** & **Soil (Concentrated erosion)** | • Sheet, rill, and wind erosion<br>• Bank, classic gully, and ephemeral gully erosion | **Partial (Co-Benefit)** | **00N**: Scen. 193, 271, 302 (Converting active annual cropland to permanent perennial cover) | **Critical Area Planting (342)** (required for severe/gully erosion), **Conservation Cover (327)**, **Filter Strip (393)**. |
| **Water (Field sediment, nutrient, pathogen, & pesticide loss)** | • Sediment from erosion sources<br>• Nonpoint N, P, pathogen, & pesticide losses | **Partial (Co-Benefit)** | **00N**: Scen. 193, 271, 302 (Taking cropland out of production & eliminating annual tillage/agrichemical inputs) | **Filter Strip (393)**, **Field Border (386)**, **Riparian Herbaceous Cover (390)**; avoid residual herbicide carryover. |
| **Soil (Soil quality limitations)** | • Organic matter depletion & compaction<br>• Aggregate instability & soil organism habitat loss<br>• Subsidence & salts/chemicals | **Partial (Co-Benefit)** | **00N**: Scen. 193, 271, 302 (Permanent deep-rooted native cover restores soil organic matter & soil biota) | **Conservation Cover (327)**; select salt/pH-adapted native species. |
| **Air (Air quality emissions)** | • GHGs - carbon stock & nitrogen fertilizer<br>• PM - windblown dust & field operations | **Partial (Co-Benefit)** | **00N**: Scen. 193, 271, 302 (Cropland conversion builds perennial carbon stock and eliminates tillage dust) | **Conservation Cover (327)**, **Field Border (386)**. |
| **Plants (Pest pressure)** | • Invasive species<br>• Plant pest pressure & chemical resistance | **No (Supporting Only)** | *Undesirable vegetation must be controlled/suppressed prior to planting (explicitly noted in Scen. 299–301)*. | **Brush Management (314)**, **Herbaceous Weed Treatment (315)**, **Pest Management Conservation System (595)**. |
| **Plants (Fire management)** | • Wildfire hazard from biomass accumulation | **No (Supporting Only)** | *Prescribed fire is used as an O&M disturbance tool to maintain native habitat structure*. | **Prescribed Burning (338)**, **Firebreak (394)**. |
