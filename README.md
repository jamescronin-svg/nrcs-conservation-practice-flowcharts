# NRCS Conservation Practice Decision Flowcharts & CAPP Mapping

This repository contains visual decision-tree flowcharts and Resource Concern mapping matrices synthesized from **NRCS Conservation Practice Standards (CPS)**, **FY Payment Scenarios**, and **CAPP Narrative Code exports**.

## 📂 Practice Index

| Practice Code | Practice Name | Flowchart & Mapping Matrix | Status |
| :--- | :--- | :--- | :--- |
| **643** | Restoration of Rare or Declining Natural Communities | [View Practice 643 Flowchart](./Practice-643-Flowchart2.md) | Active (FY 2026) |
| **390** | Riparian Herbaceous Cover | [View Practice 390 Flowchart](./Practice-390-Flowchart.md) | Active (FY 2026) |
| **420** | Wildlife Habitat Planting | [View Practice 420 Flowchart](./Practice-420-Flowchart.md) | Active (FY 2026) |
| **422** | Hedgerow Planting | [View Practice 422 Flowchart](./Practice-422-Flowchart.md) | Active (FY 2026) |
| **645** | Wildlife Habitat Management *(formerly Upland Wildlife Habitat Management)* | [View Practice 645 Flowchart](./Practice-645-Flowchart.md) | Active (FY 2026) |
| **646** | Seasonal Water Management for Wildlife | [View Practice 646 Flowchart](./Practice-646-Flowchart.md) | Active (FY 2026) |
| **649** | Structures for Wildlife | [View Practice 649 Flowchart](./Practice-649-Flowchart.md) | Active (FY 2026) |

---

## 🎨 Standard Flowchart Visual Legend

All flowcharts in this repository follow the NRCS Range/Pasture decision-tree taxonomy:

* **Brown Banner (`#833C0C`):** Primary Resource Concern(s) & CPS Purpose(s)
* **Dark Green Rectangle (`#385723`):** Primary Conservation Practice & Payment Scenario Numbers/Names
* **Light Green Rectangle (`#70AD47`):** Supporting / Associated Practices (must link to Primary)
* **Blue Oval (`#4472C4`):** Resource Considerations, Site Assessments, & Ecosystem Pathways
* **Yellow Oval (`#FFFF00`):** Planning Reasoning, Criteria, Site Conditions, & CAPP Narrative Codes
* **Black Diamond (`#000000`):** Yes / No Eligibility & Technical Decision Gates
* **Red Octagon (`#C00000`):** Stop / Exclusion Gates (*"Conditions Where Practice Does Not Apply"*)
* **Dashed Arrows (`-.->`):** Feedback to Design Primary (Monitoring, O&M, Adaptive Management)

---

## 🛠️ How to Add a New Practice Flowchart

1. Click **Add file > Create new file** in this repository.
2. Name the file `Practice-[CODE]-Flowchart.md` (e.g., `Practice-338-Flowchart.md`).
3. Generate the Mermaid diagram and mapping table using the standard synthesis prompt with the practice's **CPS PDF**, **Payment Scenarios PDF**, and **CAPP CSV export**.
4. Paste the output into the new `.md` file, verify rendering via the **Preview** tab, and commit.
5. Add a new row to the **Practice Index** table above linking to `./Practice-[CODE]-Flowchart.md`.
