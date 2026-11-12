# Practice 422: Hedgerow Planting
**Source Documents:** NRCS CPS 422 (Nov 2024), FY 2026 Practice Payment Scenarios, and CAPP Narrative/Resource Concern Data

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

    Start(["<b>Priority Resource Concerns (CPS 422):</b><br/>Terrestrial/Aquatic Habitat, Beneficial Invertebrates (IPM), Air Quality (PM/Drift/Odor), Visual/Physical Screens, Carbon Storage"]):::header
    P422["<b>Primary Practice:</b><br/>Hedgerow Planting (Code 422)"]:::primary

    Start --> P422

    %% Eligibility & Exclusion Gates (CPS 422)
    Gate_Ero{"Is primary purpose to treat erosion,<br/>nutrient transport, sediment transport,<br/>or snow/soil trapping?"}:::decision
    Stop_Ero{{"<b>DO NOT USE CODE 422</b><br/>Use Windbreak (380), Riparian Forest Buffer (391),<br/>Filter Strip (393), Veg. Barrier (601), 589C, or 311"}}:::stop

    Gate_Grass{"Is site an open grassland with<br/>area-sensitive nesting birds?"}:::decision
    Stop_Grass{{"<b>AVOID HEDGEROW PLANTING</b><br/>Linear woody cover fragments grassland<br/>& increases nest predation; use Code 420"}}:::stop

    P422 --> Gate_Ero
    Gate_Ero -->|Yes| Stop_Ero
    Gate_Ero -->|No - Meets CPS 422 Purpose| Gate_Grass
    Gate_Grass -->|Yes| Stop_Grass
    Gate_Grass -->|No - Suitable Landscape| PathSelect

    %% Pathway Selection by Narrative Code & Purpose
    PathSelect(["<b>Select Conservation Purpose & CAPP Narrative Code</b>"]):::resource

    PathSelect --> N_00(["<b>Narrative: 00N</b><br/>Wildlife Hedgerow: Woody linear cover<br/>(&ge; 1 woody row; no bunch grass alone)"]):::reasoning
    PathSelect --> N_01(["<b>Narrative: 01N</b><br/>Beetle Bank: Raised linear mound with<br/>grasses/woody plants for beneficial insects"]):::reasoning
    PathSelect --> N_02(["<b>Narrative: 02N</b><br/>Hedgerow Screen: Woody plants &amp;/or<br/>tall grasses (&ge; 3 ft) to block drift/PM/odor"]):::reasoning

    %% 00N Branch (Wildlife Hedgerow)
    N_00 --> Gate_Terrain{"Site Terrain &<br/>Planting Method?"}:::decision
    Gate_Terrain -->|"Rugged / Difficult Access<br/>(Hand Planting Required)"| Scen30["<b>Scenario 30:</b> Wildlife Hedgerow,<br/>High Labor (\$3.32/ft)"]:::primary
    Gate_Terrain -->|"Flat / Easy Access<br/>(Machine Planting Possible)"| Scen31["<b>Scenario 31:</b> Wildlife Hedgerow,<br/>Low Labor (\$2.35/ft)"]:::primary

    %% 01N Branch (Beetle Bank)
    N_01 --> Gate_IPM["Protect from pesticide drift<br/>(Follow Agronomy Tech Note 9)"]:::reasoning
    Gate_IPM --> Scen32["<b>Scenario 32:</b> Beetle Bank<br/>(\$1.92/ft)"]:::primary

    %% 02N Branch (Hedgerow Screen)
    N_02 --> Gate_Screen{"Screening / Air Quality<br/>Application Type?"}:::decision
    Gate_Screen -->|"Poultry House Exhaust Fans<br/>(Odor &amp; PM Mitigation)"| Scen29["<b>Scenario 29:</b> Grasses for Poultry House<br/>Air Quality Mitigation (\$3.23/ft)"]:::primary
    Gate_Screen -->|"Field Drift, Odor, Dust, or<br/>Visual/Noise Screen (50-65% density)"| Note_02N(["Select chemical-tolerant species;<br/>exclude pollinator-attractive plants<br/>if intercepting toxic drift"]):::reasoning

    %% Operation & Maintenance Feedback Loop
    OM(["<b>Operation & Maintenance (O&M):</b><br/>Protect from unwanted fire &amp; grazing;<br/>rejuvenate &le; 1/3 length/width outside nesting season"]):::resource
    Scen30 & Scen31 & Scen32 & Scen29 & Note_02N -.->|Feedback to Design| OM
    OM -.-> P422

    %% Supporting Practices Fallback for Non-422 Resource Concerns
    Fallback(["<b>Unresolved Spreadsheet Resource Concerns?</b><br/>(Site Prep, Irrigation/Mulch, Pollinator Diversity, Livestock, Erosion)"]):::resource
    P422 --> Fallback

    Fallback --> Supp_Est["<b>Establishment & Site Prep (CPS 422):</b><br/>Tree/Shrub Site Prep (490), Mulching (484),<br/>Microirrigation (441), Fence (382), Access Control (472)"]:::supporting
    Fallback --> Supp_Hab["<b>Habitat & Pest Augmentation (CPS 422):</b><br/>Wildlife Habitat Planting (420), Wildlife Structures (649),<br/>Pest Mgmt Conservation System (595)"]:::supporting
    Fallback --> Supp_Ero["<b>Erosion / Nutrient / Snow Trapping (Use Instead):</b><br/>Windbreak/Shelterbelt (380), Riparian Forest Buffer (391),<br/>Filter Strip (393), Vegetative Barrier (601), Alley Cropping (311)"]:::supporting
```

---

## 2. Resource Concern & Component Mapping Matrix

| Resource Concern Category (CAPP) | Resource Concern & Components (CAPP) | Direct Match to CPS 422? | Matching Narrative Code & Scenario(s) | Required Supporting Practices (from CPS 422) |
| :--- | :--- | :--- | :--- | :--- |
| **Animals (Terrestrial habitat)** | • Terrestrial habitat for wildlife and invertebrates (pollinators, corridors, winter cover) | **Yes (Primary Purpose)** | **00N**: Scen. 30 (High Labor), Scen. 31 (Low Labor) — *must include &ge; 1 woody row* | **Wildlife Habitat Planting (420)** (to achieve full bloom diversity/winter cover), **Wildlife Structures (649)** (nest boxes). |
| **Animals (Aquatic habitat)** | • Aquatic habitat for fish and other organisms<br>• Water temperature effects on aquatic habitat | **Yes (Primary Purpose)** | **00N**: Scen. 30 or 31 (provides food, cover, and shade/cooling to adjacent small watercourses) | **Riparian Forest Buffer (391)**, **Riparian Herbaceous Cover (390)** (if primary goal is streambank/nutrient buffering). |
| **Plants (Pest pressure)** | • Plant pest pressure<br>• Invasive species & chemical resistance | **Yes (Primary Purpose)** | **01N**: Scen. 32 (Beetle Bank — overwintering habitat for predaceous insects/spiders)<br>**02N**: Intercepts windblown weed seeds | **Pest Management Conservation System (595)**; follow Agronomy Tech Note 9 to protect beneficial insects from drift. |
| **Air (Air quality emissions)** | • PM - confined animal activities, windblown dust, pesticide drift, field ops<br>• Objectionable odor - confined animal activities<br>• GHGs - carbon stock | **Yes (Primary Purpose)** | **02N**: Scen. 29 (Grasses for Poultry House Air Quality Mitigation) or woody/grass screen (50–65% density)<br>**00N / 01N / 02N**: Increases biomass/soil carbon | **Windbreak/Shelterbelt Establishment (380)** (for larger multi-row wind/odor/snow systems). |
| **Soil (Wind and water erosion)** & **Soil (Concentrated erosion)** | • Sheet, rill, and wind erosion<br>• Bank, classic gully, and ephemeral gully erosion | **No (Exclusion Rule)** | *CPS 422 explicitly excludes linear plantings installed primarily to treat erosion or trap soil*. | **Windbreak/Shelterbelt (380)**, **Vegetative Barrier (601)**, **Cross Wind Trap Strips (589C)**, **Alley Cropping (311)**. |
| **Water (Field sediment, nutrient, pathogen, & pesticide loss)** | • Sediment from erosion sources<br>• Nonpoint N, P, & pathogen losses<br>• Nonpoint pesticide drift to surface water | **Partial (Drift Only)** | **02N**: Intercepts airborne **pesticide drift** (exclude pollinator plants if drift is toxic).<br>*Do not use 422 for surface runoff sediment/nutrients*. | **Filter Strip (393)**, **Riparian Forest Buffer (391)** (required to reduce surface sediment and nutrient transport). |
| **Soil (Soil quality limitations)** | • Organic matter depletion<br>• Compaction, aggregate instability, salts/chemicals, soil organism habitat | **Indirect Co-Benefit** | **00N / 01N / 02N**: Increases soil organic carbon and soil biota beneath perennial hedgerow | **Tree/Shrub Site Preparation (490)**, **Mulching (484)**, **Irrigation System, Microirrigation (441)**. |
| **Animals (Livestock production limitation)** | • Inadequate livestock shelter<br>• Feed/forage balance & livestock water | **Partial (Living Fence)** | **00N / 02N**: Living fences can restrict animal movement (use non-palatable, non-toxic, thorny species). | **Fence (382)**, **Access Control (472)** (required to protect hedgerow from grazing/browsing/trampling). |
| **Water (Weather resilience)** | • Drifted snow<br>• Ponding, flooding, drought susceptibility | **No (Exclusion Rule)** | *CPS 422 warns against undesirable snow trapping; use 380 when snow trapping is a primary purpose*. | **Windbreak/Shelterbelt Establishment (380)** (for snow management), **Microirrigation (441)** (for drought establishment). |
| **Plants (Fire management)** | • Wildfire hazard from biomass accumulation | **No (O&M Protection)** | *Hedgerows must be protected from unwanted fire throughout their lifespan (CPS 422 O&M)*. | **Firebreak (394)**, **Fuel Break (383)**. |
| **Long term protection of land, Water (Depletion/Pollutants), Air (Ozone/Reactive N), Energy** | • Threat of conversion, loss of floodplain/wetland/forest functions<br>• Groundwater/irrigation depletion, confined storage<br>• Ozone, Reactive N, Energy efficiency | **No Association** | *No 422 Payment Scenario resolves these components* (present in CSV only due to system-wide RC table cross-join). | Not addressed by CPS 422. Planner must use dedicated wetland, irrigation, waste storage, air, or energy standards. |
