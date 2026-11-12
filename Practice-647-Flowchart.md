# Practice 647: Early Successional Habitat Development–Management
**Source Documents:** NRCS CPS 647 (Nov 2022), FY 2026 Practice Payment Scenarios, and CAPP Narrative/Resource Concern Data

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

    Start(["<b>Priority Resource Concerns (CPS 647):</b><br/>Terrestrial &amp; Aquatic Wildlife Habitat (Early Successional Food, Nesting, Brood-Rearing, Escape Cover)"]):::header
    P647["<b>Primary Practice:</b><br/>Early Successional Habitat Development–Management (Code 647)"]:::primary

    Start --> P647

    %% Eligibility & Scope Gates (CPS 647)
    Elig1(["Habitat evaluation shows site is static/trending to late succession<br/>AND native seed bank / rootstock can regenerate post-disturbance"]):::resource
    Gate_Seed{"Is native seed bank depleted<br/>(seeding/planting required)?"}:::decision
    Stop_Seed{{"<b>SEEDING REQUIRED FIRST</b><br/>Use Wildlife Habitat Planting (420),<br/>Conservation Cover (327), or Range Planting (550)"}}:::stop

    Gate_Purpose{"Is primary objective timber production<br/>or invasive weed eradication alone?"}:::decision
    Stop_Purpose{{"<b>OUT OF SCOPE FOR 647</b><br/>Use Forest Stand Improvement (666),<br/>Brush Mgmt (314), or Weed Treatment (315)"}}:::stop

    P647 --> Elig1 --> Gate_Seed
    Gate_Seed -->|Yes| Stop_Seed
    Gate_Seed -->|No - Adequate Seed Bank| Gate_Purpose
    Gate_Purpose -->|Yes| Stop_Purpose
    Gate_Purpose -->|No - Set Back Succession for Habitat| PathSelect

    %% Pathway Selection by CAPP Narrative Code
    PathSelect(["<b>Select Program / Objective &amp; CAPP Narrative Code</b>"]):::resource

    PathSelect --> N_CRP(["<b>Narrative: 00N-CRP-R</b><br/>CRP Re-enrollment: Maintain existing<br/>early successional habitat"]):::reasoning
    PathSelect --> N_00(["<b>Narrative: 00N</b><br/>Early Successional Habitat: Manage plant<br/>succession to develop/maintain early seral stage"]):::reasoning

    %% 00N-CRP-R Branch
    N_CRP --> CRP_Note(["Apply rotational disturbance (&le; 1/3 per year)<br/>per CRP contract outside nesting season."]):::reasoning

    %% 00N Branch (Scenario Selection by Existing Cover Type)
    N_00 --> Gate_Cover{"Existing Vegetative Cover &amp;<br/>Landscape Setting?"}:::decision

    %% Branch 1: Herbaceous / Field Edge / Pasture
    Gate_Cover -->|"1. Open Herbaceous / Pasture /<br/>Field Edge / Pivot Corner"| Gate_Herb{"Primary Disturbance Goal:<br/>Height Diversity vs. Bare Ground?"}:::decision
    Gate_Herb -->|"Mowing Woody Encroachment &amp;<br/>Create Height Heterogeneity"| Scen1["<b>Scenario 1:</b> Mowing<br/>(\$327.33/ac)"]:::primary
    Gate_Herb -->|"Disking Dense Sod to Create<br/>Bare Ground for Annual Forbs"| Scen2["<b>Scenario 2:</b> Disking<br/>(\$204.93/ac)"]:::primary

    %% Branch 2: Forest-to-Field Hard Edge
    Gate_Cover -->|"2. Abrupt Forest-to-Field<br/>Transition ('Hard Edge')"| Scen49["<b>Scenario 49:</b> Edge Feathering<br/>(30–50 ft felled shrub zone; \$808.55/ac)"]:::primary

    %% Branch 3: Overgrown Scrub-Shrub
    Gate_Cover -->|"3. Overgrown / Closed-Canopy<br/>Scrub-Shrub Stand"| Scen70["<b>Scenario 70:</b> Creating Early Successional Habitat<br/>in Overgrown Scrub-Shrub (\$1,490.52/ac)"]:::primary

    %% Branch 4: Closed-Canopy / Degraded Forest
    Gate_Cover -->|"4. Closed-Canopy or<br/>Degraded Forest Stand"| Gate_ForMethod{"Tree Removal Method:<br/>Hand Tools vs. Heavy Machinery?"}:::decision
    Gate_ForMethod -->|"Hand Tools (Chainsaws +<br/>Stump Herbicide)"| Scen91["<b>Scenario 91:</b> Creating Early Successional Habitat<br/>Forest Opening w/ Hand Tools (\$1,862.80/ac)"]:::primary
    Gate_ForMethod -->|"Heavy Machinery (Dozer /<br/>Mechanical Clearing)"| Scen112["<b>Scenario 112:</b> Creating Early Successional Habitat<br/>Forest Opening w/ Machinery (\$2,006.66/ac)"]:::primary

    %% Operation & Maintenance Feedback Loop
    OM(["<b>Operation &amp; Maintenance (CPS 647):</b><br/>Rotate treatments across adjacent blocks every 2–5 yrs before canopy closure;<br/>schedule disturbances outside primary nesting/brood-rearing seasons"]):::resource
    Scen1 & Scen2 & Scen49 & Scen70 & Scen91 & Scen112 -.->|Feedback to Design| OM
    OM -.-> P647

    %% Supporting Practices Fallback for Non-647 Resource Concerns
    Fallback(["<b>Unresolved Spreadsheet Resource Concerns?</b><br/>(Prescribed Fire, Invasive Weeds, Supplemental Seeding, Erosion, Livestock)"]):::resource
    P647 --> Fallback

    Fallback --> Supp_Dist["<b>Disturbance &amp; Invasive Control (CPS 647):</b><br/>Prescribed Burning (338), Firebreak (394), Brush Mgmt (314),<br/>Herbaceous Weed Treatment (315), Woody Residue Treatment (384)"]:::supporting
    Fallback --> Supp_Veg["<b>Supplemental Seeding &amp; Forest Mgmt (CPS 647):</b><br/>Wildlife Habitat Planting (420), Conservation Cover (327),<br/>Range Planting (550), Forest Stand Improvement (666)"]:::supporting
    Fallback --> Supp_Prot["<b>Erosion &amp; Livestock Management (CPS 647):</b><br/>Prescribed Grazing (528), Fence (382), Access Control (472),<br/>Critical Area Planting (342)"]:::supporting
```

---

## 2. Resource Concern & Component Mapping Matrix

| Resource Concern Category (CAPP) | Resource Concern & Components (CAPP) | Direct Match to CPS 647? | Matching Narrative Code & Scenario(s) | Required Supporting Practices (from CPS 647) |
| :--- | :--- | :--- | :--- | :--- |
| **Animals (Terrestrial habitat)** | • Terrestrial habitat for wildlife and invertebrates (brood-rearing bare ground, annual forbs, soft-mast shrubs, feathered forest edges, forest openings) | **Yes (Primary Purpose)** | **00N**:<br>• **Herbaceous/Pasture**: Scen. 1 (Mowing), Scen. 2 (Disking)<br>• **Forest Edge**: Scen. 49 (Edge Feathering)<br>• **Scrub-Shrub**: Scen. 70<br>• **Forest Opening**: Scen. 91 (Hand), Scen. 112 (Machine)<br>**00N-CRP-R**: CRP Maintenance | **Prescribed Burning (338)**, **Wildlife Habitat Planting (420)** (if seed bank is lacking), **Structures for Wildlife (649)** (brush piles/snags from felled trees). |
| **Animals (Aquatic habitat)** | • Aquatic habitat for fish and other organisms<br>• Water temperature effects on aquatic habitat | **Partial (Riparian Transition)** | **00N**: Scen. 1 (Mowing) or Scen. 49 (Edge Feathering) along transitional upland/riparian edges (*maintain shading buffer directly over stream*) | **Riparian Herbaceous Cover (390)**, **Riparian Forest Buffer (391)** (do not remove canopy shading where water temperature is a concern). |
| **Plants (Degraded plant condition)** | • Plant productivity and health<br>• Plant structure and composition | **Yes (Primary Purpose)** | **00N**: Scen. 1, 2, 49, 70, 91, 112 (Breaks up monotypic sod/closed canopy to restore structural &amp; forb diversity) | **Prescribed Grazing (528)**, **Forest Stand Improvement (666)**, **Range Planting (550)**. |
| **Plants (Pest pressure)** | • Invasive species<br>• Plant pest pressure &amp; chemical resistance | **No (Supporting / Caution)** | *Soil disturbance (Scen. 2 Disking) and canopy opening (Scen. 70, 91, 112) can stimulate dormant invasive weeds if not pre-treated*. | **Brush Management (314)**, **Herbaceous Weed Treatment (315)**, **Pest Management Conservation System (595)**. |
| **Plants (Fire management)** | • Wildfire hazard from biomass accumulation | **Partial (Fuel Reduction / Residue)** | **00N**: Scen. 1 (Mowing) &amp; Scen. 70 (Mulching) reduce dense standing thatch/shrub fuel loads; *manage felled slash in Scen. 49, 91, 112* | **Prescribed Burning (338)**, **Firebreak (394)**, **Woody Residue Treatment (384)**. |
| **Soil (Wind and water erosion)** & **Soil (Concentrated erosion)** | • Sheet, rill, wind, bank, and gully erosion | **No (Caution / Supporting)** | *Avoid Scen. 2 (Disking) and Scen. 112 (Dozer) on steep/erodible slopes or concentrated flow areas; follow soil loss tolerance (T)*. | **Critical Area Planting (342)**, **Conservation Cover (327)**, **Filter Strip (393)**. |
| **Animals (Livestock production limitation)** | • Feed and forage balance<br>• Inadequate livestock shelter &amp; water | **No (Supporting / Grazing Interface)** | *CPS 647 is not for livestock forage production; grazing may be used post-disturbance as a management tool*. | **Prescribed Grazing (528)**, **Fence (382)**, **Access Control (472)**. |
| **Soil (Soil quality), Water (Quality/Quantity/Resilience), Long term protection, Air, Energy** | • Compaction, organic matter, salts, subsidence<br>• Sediment, nutrients, pathogens, pesticides, depletion<br>• Threat of conversion, GHGs, Odor, Ozone, PM, Energy | **No Association** | *No 647 Payment Scenario resolves these components* (present in CSV only due to system-wide RC table cross-join). | Not addressed by CPS 647. Planner must use dedicated soil health, water quality, irrigation, air, or energy standards. |
