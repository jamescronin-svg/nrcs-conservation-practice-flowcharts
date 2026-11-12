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
