# Practice 645: Wildlife Habitat Management
**Source Documents:** NRCS CPS 645 (Jan 2026), FY 2026 Practice Payment Scenarios, and CAPP Narrative/Resource Concern Data *(listed in CAPP as Upland Wildlife Habitat Management)*

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

    Start(["<b>Priority Resource Concern (CPS 645):</b><br/>Terrestrial Habitat for Wildlife & Invertebrates (Food, Cover, Connectivity, Conflict Reduction)"]):::header
    P645["<b>Primary Practice:</b><br/>Wildlife Habitat Management (Code 645)"]:::primary

    Start --> P645

    %% Eligibility & Specificity Gates (CPS 645)
    Elig1(["Complete State-Approved Wildlife Habitat Evaluation (WHEG)<br/>to identify limiting habitat factors"]):::resource
    Gate_Spec{"Does a MORE SPECIFIC NRCS practice exist<br/>for the primary action needed?"}:::decision
    Stop_Spec{{"<b>DO NOT USE CODE 645</b><br/>Use specific standard instead: Perennial Planting (420),<br/>Early Successional (647), Wetland (644), Aquatic (395),<br/>Structures (649), Burn (338), or Grazing (528)"}}:::stop

    P645 --> Elig1 --> Gate_Spec
    Gate_Spec -->|Yes| Stop_Spec
    Gate_Spec -->|No - 645 is Best Fit| PathSelect

    %% Pathway Selection by CAPP Narrative Code
    PathSelect(["<b>Select Planning Objective & CAPP Narrative Code</b>"]):::resource

    PathSelect --> N_00(["<b>Narrative: 00N</b><br/>Standard Mgmt: Enable movement &amp;/or<br/>provide food/cover to meet min. WHEG criteria"]):::reasoning
    PathSelect --> N_01(["<b>Narrative: 01N</b><br/>High Enhancement: Exceed &amp; improve upon<br/>WHEG criteria (even if baseline already passes)"]):::reasoning

    %% Action Type Routing (Applies to both 00N and 01N)
    N_00 & N_01 --> Gate_Action{"Select Target Habitat Management Action"}:::decision

    %% Branch 1: Seasonal Annual Food / Cover
    Gate_Action -->|"Plant Annual Seasonal<br/>Food or Cover"| Gate_Crop{"Land Use &amp; Cropping<br/>Season Impact?"}:::decision
    Gate_Crop -->|"Non-Cropland<br/>(Mow, Disk, Cultipack + NPK)"| Scen327["<b>Scenario 327:</b> Establishment of Seasonal Forage<br/>or Cover on Non-Cropland (\$449.35/ac)"]:::primary
    Gate_Crop -->|"Cropland - In Lieu of Cash Crop<br/>(Includes Foregone Income)"| Scen392["<b>Scenario 392:</b> Seasonal Forage/Cover on<br/>Cropland, Foregone Income (\$694.58/ac)"]:::primary
    Gate_Crop -->|"Cropland - Outside Crop Season<br/>(No Foregone Income)"| Scen393["<b>Scenario 393:</b> Seasonal Forage/Cover on<br/>Cropland, w/o Foregone Income (\$223.62/ac)"]:::primary

    %% Branch 2: Structural / Successional Disturbance
    Gate_Action -->|"Set Back Succession /<br/>Increase Structural Diversity"| Gate_Dist{"Disturbance Method &amp;<br/>Bare Ground Need?"}:::decision
    Gate_Dist -->|"Mowing Woody Encroachment /<br/>Create Height Heterogeneity"| Scen586["<b>Scenario 586:</b> Mowing<br/>(\$327.33/ac)"]:::primary
    Gate_Dist -->|"Disking Dense Sod /<br/>Create Bare Ground for Forbs"| Scen607["<b>Scenario 607:</b> Disking<br/>(\$204.93/ac)"]:::primary

    %% Branch 3: Crop Harvest Timing
    Gate_Action -->|"Modify Crop Harvest Timing<br/>for Nesting Birds"| Scen628["<b>Scenario 628:</b> Delayed Harvest,<br/>Silage-Corn Rotation (\$815.04/ac)"]:::primary

    %% Branch 4: Movement Connectivity & Conflict Deterrence
    Gate_Action -->|"Wildlife Movement Passage<br/>or Carnivore Deterrence"| Gate_Fence{"Passage Modification vs.<br/>Predator Deterrence?"}:::decision
    Gate_Fence -->|"Big Game Migration Passage<br/>(Cameras + Adjustable/Lay-Down Fence)"| Scen397["<b>Scenario 397:</b> Monitoring &amp; Mgmt of Adjustable-Wire,<br/>Lay-Down Fence &amp; Gates (\$0.12/ft)"]:::primary
    Gate_Fence -->|"At-Risk Carnivore Deterrence<br/>(Turbo Fladry - Year 1 Install)"| Scen398["<b>Scenario 398:</b> Turbo Fladry Carnivore<br/>Deterrent Fence, Year One (\$1.95/ft)"]:::primary
    Gate_Fence -->|"At-Risk Carnivore Deterrence<br/>(Turbo Fladry - Years 2–5 Reinstall)"| Scen399["<b>Scenario 399:</b> Turbo Fladry Carnivore<br/>Deterrent Fence, Yrs 2–5 (\$0.55/ft)"]:::primary

    %% Monitoring & Adaptive Management Feedback Loop
    OM(["<b>Monitoring &amp; Adaptive Management (CPS 645):</b><br/>Re-evaluate WHEG post-treatment; time disturbances<br/>outside nesting/brood-rearing; verify agency coordination"]):::resource
    Scen327 & Scen392 & Scen393 & Scen586 & Scen607 & Scen628 & Scen397 & Scen398 & Scen399 -.->|Feedback to Design| OM
    OM -.-> P645

    %% Supporting Practices Fallback for Non-645 Resource Concerns
    Fallback(["<b>Unresolved Spreadsheet Resource Concerns?</b><br/>(Perennial Cover, Fence Retrofits, Invasive Weeds, Erosion, Water)"]):::resource
    P645 --> Fallback

    Fallback --> Supp_Hab["<b>Companion Habitat &amp; Structural Practices:</b><br/>Wildlife Habitat Planting (420), Structures for Wildlife (649),<br/>Fence (382), Early Successional Habitat (647), Wetland Mgmt (644)"]:::supporting
    Fallback --> Supp_Mgmt["<b>Disturbance &amp; Pest Management:</b><br/>Prescribed Burning (338), Prescribed Grazing (528),<br/>Brush Mgmt (314), Herbaceous Weed Treatment (315), IPM (595)"]:::supporting
    Fallback --> Supp_Ero["<b>Erosion, Buffer &amp; Watering Practices:</b><br/>Conservation Cover (327), Field Border (386), Filter Strip (393),<br/>Critical Area Planting (342), Watering Facility (614)"]:::supporting
```

---

## 2. Resource Concern & Component Mapping Matrix

| Resource Concern Category (CAPP) | Resource Concern & Components (CAPP) | Direct Match to CPS 645? | Matching Narrative Code & Scenario(s) | Required Supporting Practices (from CPS 645) |
| :--- | :--- | :--- | :--- | :--- |
| **Animals (Terrestrial habitat)** | • Terrestrial habitat for wildlife and invertebrates (food, seasonal cover, nesting/brood-rearing, migration connectivity, reducing carnivore habitat sinks) | **Yes (Primary Purpose)** | **00N** (Meet min. WHEG) & **01N** (Exceed WHEG):<br>• **Annual Food/Cover**: Scen. 327, 392, 393<br>• **Succession/Structure**: Scen. 586 (Mowing), 607 (Disking)<br>• **Nesting Timing**: Scen. 628 (Delayed Harvest)<br>• **Connectivity/Deterrence**: Scen. 397, 398, 399 | **Wildlife Habitat Planting (420)** (for perennial cover), **Structures for Wildlife (649)** (fence retrofits/nest boxes), **Fence (382)**, **Early Successional Habitat (647)**. |
| **Plants (Degraded plant condition)** | • Plant productivity and health<br>• Plant structure and composition | **Partial (Structural Goal)** | **00N / 01N**: Scen. 586 (Mowing) & Scen. 607 (Disking) set back succession and increase structural/forb heterogeneity | **Prescribed Burning (338)**, **Prescribed Grazing (528)**, **Range Planting (550)**, **Forest Stand Improvement (666)**. |
| **Soil (Wind and water erosion)** & **Soil (Concentrated erosion)** | • Sheet, rill, and wind erosion<br>• Bank, classic gully, and ephemeral gully erosion | **Partial (Off-Season Cover / Caution)** | **00N / 01N**: Scen. 393 (off-season annual cover reduces winter erosion); *use caution with Scen. 607 (Disking) on erodible slopes* | **Conservation Cover (327)**, **Critical Area Planting (342)**, **Cover Crop (340)**; follow soil loss tolerance (T) limits when disking. |
| **Plants (Pest pressure)** | • Invasive species<br>• Plant pest pressure & chemical resistance | **No (Supporting / IPM)** | *CPS 645 avoids non-native/invasive species; beneficial insect habitat supports IPM*. | **Pest Management Conservation System (595)**, **Brush Management (314)**, **Herbaceous Weed Treatment (315)**, **Hedgerow Planting (422)** (Beetle Bank). |
| **Animals (Livestock production limitation)** | • Inadequate livestock shelter & water<br>• Feed and forage balance | **Partial (Conflict / Fence Interface)** | **00N / 01N**: Scen. 397 (adjustable/lay-down livestock fences), Scen. 398 & 399 (Turbo Fladry protects vulnerable livestock from wolves) | **Fence (382)** (wildlife-friendly design), **Prescribed Grazing (528)**, **Watering Facility (614)** (with wildlife escape ramps). |
| **Water (Field sediment, nutrient, pathogen, & pesticide loss)** | • Sediment from erosion sources<br>• Nonpoint N, P, pathogen, & pesticide losses | **Indirect Co-Benefit** | **00N / 01N**: Scen. 392 & 393 (annual cover scavenges residual N and reduces runoff); *protect habitat from pesticide drift* | **Filter Strip (393)**, **Field Border (386)**, **Riparian Herbaceous Cover (390)**, **Pest Management (595)**. |
| **Animals (Aquatic habitat)** | • Aquatic habitat for fish and other organisms<br>• Water temperature effects on aquatic habitat | **No (Use Specific Standard)** | *CPS 645 directs planners to use specific aquatic/wetland standards when primary habitat is aquatic*. | **Stream Habitat Improvement & Management (395)**, **Wetland Wildlife Habitat Management (644)**, **Riparian Forest Buffer (391)**. |
| **Plants (Fire management)** & **Soil (Soil quality limitations)** | • Wildfire hazard from biomass accumulation<br>• Organic matter depletion, compaction, salts | **No (Supporting / Indirect)** | *Mowing (Scen. 586) reduces woody fuel accumulation; annual cover adds organic matter*. | **Prescribed Burning (338)**, **Firebreak (394)**, **Soil Carbon Amendment (336)**. |
