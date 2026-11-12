# Practice 390: Riparian Herbaceous Cover
**Source Documents:** NRCS CPS 390 (Nov 2022), FY 2026 Practice Payment Scenarios, and CAPP Narrative/Resource Concern Data

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

    Start(["<b>Priority Resource Concerns (CPS 390):</b><br/>Water Quality/Quantity, Streambank Stability, Fish & Wildlife/Pollinator Habitat, Plant Condition"]):::header
    P390["<b>Primary Practice:</b><br/>Riparian Herbaceous Cover (Code 390)"]:::primary

    Start --> P390

    %% Eligibility & Site Assessment Gates
    Elig1(["Site is transitional zone adjacent to perennial, intermittent, or ephemeral watercourse/waterbody"]):::resource
    Gate_Bank{"Is channel & streambank stability<br/>adequate to support practice?"}:::decision
    Stop_Bank{{"<b>DO NOT INSTALL 390 ALONE</b><br/>Stabilize channel/banks first using<br/>Streambank & Shoreline Protection (580)"}}:::stop

    Gate_Seed{"Is native seed bank present &<br/>natural regeneration adequate?"}:::decision
    Stop_Seed{{"<b>PLANTING NOT REQUIRED</b><br/>Use natural regeneration + Access Control (472)<br/>or Prescribed Grazing (528)"}}:::stop

    P390 --> Elig1 --> Gate_Bank
    Gate_Bank -->|No - Unstable Banks| Stop_Bank
    Gate_Bank -->|Yes| Gate_Seed
    Gate_Seed -->|Yes| Stop_Seed
    Gate_Seed -->|No - Seeding/Plugging Needed| PathSelect

    %% Pathway Selection by Narrative Code & Purpose
    PathSelect(["<b>Select Primary Objective & CAPP Narrative Code</b>"]):::resource

    PathSelect --> N_CRP(["<b>Narrative: 00N-CRP-R</b><br/>CRP Re-enrollment: Maintain existing<br/>riparian herbaceous cover"]):::reasoning
    PathSelect --> N_00(["<b>Narrative: 00N</b><br/>Basic Riparian Cover: Narrow strip<br/>(min. 2.5x stream width or 35 ft)<br/>to slow water & trap nutrients"]):::reasoning
    PathSelect --> N_01(["<b>Narrative: 01N</b><br/>Fish & Wildlife Design: Wide strip<br/>with diverse native grasses, forbs,<br/>& varying bloom times"]):::reasoning
    PathSelect --> N_0203(["<b>Narratives: 02N & 03N</b><br/>Width Expansion: Increase width of<br/>existing cover to boost efficacy"]):::reasoning

    %% 00N-CRP-R Branch
    N_CRP --> CRP_Note(["Manage existing stand per CRP contract.<br/>Mow/disturb &le; 1/3 per year outside<br/>nesting/fawning season."]):::reasoning

    %% Scenario Selection Gate for 00N, 01N, 02N, 03N
    N_00 & N_01 & N_0203 --> Gate_Mix{"Select Species Mix &<br/>Establishment Method"}:::decision

    Gate_Mix -->|"Stiff-stemmed grasses only<br/>(Water Quality / Bank Stability)"| Scen39["<b>Scenario 39: Grass</b><br/>No-till/range drill adapted grasses<br/>($1,026.38/ac)"]:::primary
    Gate_Mix -->|"Standard Native Grass & Forbs<br/>(Wildlife / Pollinator Diversity)"| Scen40["<b>Scenario 40: Native Grass and Forbs</b><br/>Diverse native grass & forb mix<br/>($1,026.38/ac)"]:::primary
    Gate_Mix -->|"Specialized / High-Cost Seed<br/>(Specific Ecological Site / Habitat)"| Scen41["<b>Scenario 41: Specialized Seed</b><br/>Specialized native seed mix<br/>($1,443.13/ac)"]:::primary
    Gate_Mix -->|"Severe Hydrology / Scour Risk<br/>(Requires Live Sprigs + Seed)"| Scen44["<b>Scenario 44: Plugging and Seeding</b><br/>Combined seeding & live sprigging<br/>($7,038.68/ac)"]:::primary

    %% Operation & Maintenance Feedback Loop
    OM(["<b>Operation & Maintenance (O&M):</b><br/>Defer grazing &ge; 2 yrs until established;<br/>control pests; inspect up-gradient erosion"]):::resource
    Scen39 & Scen40 & Scen41 & Scen44 -.->|Feedback to Design| OM
    OM -.-> P390

    %% Supporting Practices Fallback for Non-390 Resource Concerns
    Fallback(["<b>Unresolved Spreadsheet Resource Concerns?</b><br/>(Livestock Access, Up-Gradient Erosion, Invasive Weeds, Woody Cover)"]):::resource
    P390 --> Fallback

    Fallback --> Supp_Liv["<b>Livestock & Access Control (CPS 390):</b><br/>Fence (382), Access Control (472), Prescribed Grazing (528A),<br/>Stream Crossing (578), Watering Facility (614), Heavy Use Area (561)"]:::supporting
    Fallback --> Supp_Ero["<b>Up-Gradient & Bank Stabilization (CPS 390):</b><br/>Streambank Protection (580), Critical Area Planting (342),<br/>Filter Strip (393), Stream Habitat Imp. (395)"]:::supporting
    Fallback --> Supp_Veg["<b>Site Prep, Pest & Habitat Mgmt (CPS 390):</b><br/>Brush Mgmt (314), Herbaceous Weed Treatment (315),<br/>Riparian Forest Buffer (391), Conservation Cover (327),<br/>Early Successional Habitat (647)"]:::supporting
```

---

## 2. Resource Concern & Component Mapping Matrix

| Resource Concern Category (CAPP) | Resource Concern & Components (CAPP) | Direct Match to CPS 390? | Matching Narrative Code & Scenario(s) | Required Supporting Practices (from CPS 390) |
| :--- | :--- | :--- | :--- | :--- |
| **Water (Field sediment, nutrient and pathogen loss)** | • Sediment from erosion sources<br>• Nonpoint N & P (surface & groundwater)<br>• Nonpoint pathogens (surface & groundwater) | **Yes (Primary Purpose)** | **00N**: Scen. 39 (Grass - stiff stems)<br>**02N / 03N**: Scen. 39 or 40 (Width expansion)<br>**00N-CRP-R**: CRP Maintenance | **Filter Strip (393)**, **Critical Area Planting (342)**; replace/regulate existing underground drains passing through buffer. |
| **Water (Field pesticide loss)** & **Water (Salt losses to water)** | • Nonpoint pesticide drift, leaching, & surface loss<br>• Salt loss to surface & groundwater | **Yes (Primary Purpose)** | **00N**: Scen. 39 (Grass - stiff stems)<br>**02N / 03N**: Scen. 39 or 40 (Width expansion) | **Filter Strip (393)**; select plant species tolerant to locally used herbicides. |
| **Soil (Concentrated erosion)** & **Soil (Wind and water erosion)** | • Bank erosion from streams/shorelines<br>• Classic & ephemeral gully erosion<br>• Sheet, rill, and wind erosion | **Yes (Primary Purpose)** | **00N / 02N / 03N**: Scen. 39 (deep-binding root mass) or Scen. 44 (Plugging & Seeding for high-energy sites) | **Streambank & Shoreline Protection (580)** (required if banks are unstable), **Critical Area Planting (342)**; control up-gradient concentrated flow first. |
| **Animals (Aquatic habitat)** | • Aquatic habitat for fish and other organisms<br>• Water temperature effects on aquatic habitat | **Yes (Primary Purpose)** | **01N**: Scen. 40 (Native Grass & Forbs), Scen. 41 (Specialized Seed), Scen. 44 (Plugging & Seeding) | **Stream Habitat Improvement & Management (395)**, **Riparian Forest Buffer (391)** (for larger stream shading), **Stream Crossing (578)**. |
| **Animals (Terrestrial habitat)** | • Terrestrial habitat for wildlife and invertebrates (including pollinators) | **Yes (Primary Purpose)** | **01N**: Scen. 40 (Native Grass & Forbs), Scen. 41 (Specialized Seed), Scen. 44 (Plugging & Seeding)<br>**00N-CRP-R**: CRP Maintenance | **Conservation Cover (327)**, **Early Successional Habitat Development (647)**; disturb &le; 1/3 of stand annually outside nesting/fawning season. |
| **Plants (Degraded plant condition)** | • Plant productivity and health<br>• Plant structure and composition | **Yes (Primary Purpose)** | **00N / 01N / 02N / 03N**: Scen. 39, 40, 41, or 44 (based on ESD State & Transition model)<br>**00N-CRP-R**: CRP Maintenance | **Pasture and Hayland Planting (512)**, **Range Planting (550)**, **Prescribed Grazing (528A)**. |
| **Water (Weather resilience)** & **Water (Source water depletion)** | • Ponding and flooding (floodplain storage)<br>• Seasonal high water table, seeps, drought<br>• Surface/groundwater depletion, drifted snow | **Partial (Secondary)** | **00N / 01N / 02N / 03N**: All Scenarios (increases floodplain water storage & infiltration) | **Stream Habitat Improvement (395)**; select species adapted to projected duration of inundation/saturation. |
| **Air (Air quality emissions)** | • GHGs - carbon stock<br>• PM - windblown dust & field operations | **Partial (Primary / Secondary)** | **01N / 02N / 03N**: Scen. 40, 41, or 44 (maximize width/length & high-biomass species for net carbon storage) | **Conservation Cover (327)**; use species providing full ground coverage to minimize PM during establishment. |
| **Plants (Pest pressure)** | • Invasive species<br>• Plant pest pressure & chemical resistance | **No (Supporting Only)** | *Must control invasive trees/shrubs & noxious weeds before/during establishment*. | **Brush Management (314)**, **Herbaceous Weed Treatment (315)** (conduct in a manner that mitigates pollinator impacts). |
| **Animals (Livestock production limitation)** | • Inadequate livestock water quantity/quality/distribution<br>• Feed/forage balance & shelter | **No (Supporting Only)** | *Grazing must be deferred &ge; 2 years until established; practice provides secondary livestock forage once established*. | **Fence (382)**, **Access Control (472)**, **Watering Facility (614)**, **Stream Crossing (578)**, **Heavy Use Area Protection (561)**, **Prescribed Grazing (528A)**. |
| **Soil (Soil quality limitations)** & **Long term protection of land** | • Compaction, aggregate instability, organic matter<br>• Loss of floodplain/wetland/forestland functions | **Indirect Co-Benefit** | **00N / 01N / 02N / 03N**: Deep root systems improve soil health and restore floodplain functions | **Riparian Forest Buffer (391)** (for forestland functions), **Prescribed Grazing (528A)** (to prevent bank compaction). |
