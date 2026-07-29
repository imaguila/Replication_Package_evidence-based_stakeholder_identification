

# Replication Package:  evidence-based stakeholder identification .....

Replication Package: Evidence-based stakeholder identification and conflict management in a requirements prioritisation context
This repository contains the replication package and datasets for the paper "Evidence-based stakeholder identification and conflict management in a requirements prioritisation context" by José del Sagrado and Isabel M. del Águila (Department of Informatics, University of Almería).


## Overview

The dataset provides the experimental data used to evaluate the proposed operationalization method for identifying stakeholder salience based on three core attributes: **Urgency (`urg`)**, **Legitimacy (`leg`)**, and **Power (`pow`)**. 

The source metrics are derived from the original RALIC project dataset, which is publicly available at [Sooling Lim's Dataset Repository](https://soolinglim.com/Datasets.html). To evaluate effectiveness in maintaining equality and diversity, the arrangement model is systematically evaluated by mapping these stakeholder attributes into **two and three intervals** per dimension, producing distinct stakeholder **subgroups**.


Identifying key stakeholders and managing conflicting subjective perceptions are critical challenges in Software Engineering and Requirements Engineering. This package provides the experimental datasets and results used to evaluate an automated key stakeholder identification methodology based on Evidence Theory (Dempster-Shafer Theory).

The methodology transforms subjective peer recommendations gathered from a stakeholder recommendation network into Basic Probability Assignments (BPAs) and aggregates them using two main combination paradigms:

 - **Average Rule (AR)**: A conflict-neutralizing baseline.

- **Hybrid Combination Rule (HCR)**: A dynamic, adaptive rule that redistributes conflict based on agreement and maximum disagreement.

The evaluation uses the empirical RALIC project dataset (Replacement Access, Library and ID Card project at University College London) across its two recommendation networks (OpenR and ClosedR). Furthermore, the repository includes datasets assessing the impact of stakeholder reduction on requirements prioritisation under three preference elicitation methods (Ranking, Rating, and 100-Points).


---

## Repository Structure

The repository contains 12 core `.csv` files organized into three functional categories:

### 1. Recommendation Networks (Source Data)
* `openR_recommendations.csv`: Recommendation matrix for the **OpenR** network (61 recommenders $\times$ 127 candidate stakeholders) with ratings on an 8-point scale (0 to 8).
* `closed_recommendations.csv`: Recommendation matrix for the **ClosedR** network (50 recommenders $\times$ 76 candidate stakeholders) with ratings on a 10-point scale (0 to 10).

### 2. Identified Key Stakeholders & Aggregated BPAs (Results)
* `open_stks_avg.csv`: Aggregated Basic Probability Assignments (BPAs) for key stakeholders identified in OpenR using the **Average Rule (AR)** ($\alpha \ge 0.10$).
* `open_stks_hyb.csv`: Aggregated BPAs for key stakeholders identified in OpenR using the **Hybrid Combination Rule (HCR)** ($\alpha \ge 0.10$).
* `close_stks_avg.csv`: Aggregated BPAs for key stakeholders identified in ClosedR using the **Average Rule (AR)** ($\alpha \ge 0.10$).
* `close_stks_hyb.csv`: Aggregated BPAs for key stakeholders identified in ClosedR using the **Hybrid Combination Rule (HCR)** ($\alpha \ge 0.10$).

### 3. Requirements & Prioritisation Datasets
* `RalicReqDataOpen.csv`: Effort estimates and aggregated satisfaction metrics per requirement for the OpenR network.
* `RalicReqDataClose.csv`: Effort estimates and aggregated satisfaction metrics per requirement for the ClosedR network.
* `RalicReqStkDataOpenRank.csv`: Individual stakeholder preference rankings for OpenR requirements.
* `RalicReqStkDataOpenRate.csv`: Individual stakeholder preference ratings (scale 0–5, -1) for OpenR requirements.
* `RalicReqStkDataCloseRank.csv`: Individual stakeholder preference rankings for ClosedR requirements.
* `RalicReqStkDataCloseRate.csv`: Individual stakeholder preference ratings for ClosedR requirements.

---

## Data Formats & Schemas

### Category A: Recommendation Networks (`openR_recommendations.csv`, `closed_recommendations.csv`)

* **Format:** Comma-separated values (`,`), double-quoted strings.
* **Structure:** The first column contains the recommender's name. Headers list all candidate recommendees/stakeholders. Each cell represents the subjective influence rating assigned by the recommender to the recommendee.

| Column | Type | Description |
| :--- | :--- | :--- |
| `Recommender` (Col 1) | String | Name of the evaluating stakeholder giving recommendations. |
| `[Stakeholder_Name]` (Cols 2+) | Integer | Influence score assigned to the candidate stakeholder. OpenR: 0 (*None*) to 8 (*Total*); ClosedR: 0 (*None*) to 10 (*Total*). |

**Data Example (`openR_recommendations.csv`):**
```csv
"Derek Pack","Greg Beech","Stella Wigs","Jim Howe","John Poole","Martin Payne",...
"Aaron Toms",3,3,3,3,3,7,...
"Alison Crane",1,1,1,1,1,1,...
```

---

### Category B: Identified Key Stakeholders (`open_stks_avg.csv`, `open_stks_hyb.csv`, `close_stks_avg.csv`, `close_stks_hyb.csv`)

* **Format:** Comma-separated values (`,`).
* **Structure:** Single-row dataset where column headers correspond to the identified key stakeholders (filtered by significance threshold $\alpha = 0.10$), and values represent their aggregated consensus mass assignment (BPA).

| Column | Type | Description |
| :--- | :--- | :--- |
| `[Stakeholder_Name]` | String | Column header representing an identified key stakeholder. |
| `BPA Value` (Row 1) | Float | Aggregated Basic Probability Assignment value ($m(stk_i)$) reflecting consensus influence. |

**Data Example (`open_stks_hyb.csv`):**
```csv
"Martin.Payne","Mike.Dawson","Jan.Crowe","Barbara.Song","David.Shaffer","Ian.More","Johnny.Glenn"
0.0198314533123557,0.0576668659867703,0.0346189670018628,0.177304662198424,0.148177907052512,0.089700507644264,0.0840325176969092
```

---

### Category C: Requirement Metrics (`RalicReqDataOpen.csv`, `RalicReqDataClose.csv`)

* **Format:** Semicolon-separated values (`;`).
* **Structure:** Summary dataset containing effort and overall satisfaction for 147 project requirements.

| Column | Type | Description |
| :--- | :--- | :--- |
| `ReqID` | String | Unique requirement identifier code (e.g., `"a.1"`, `"a.1.1"`). |
| `Effort` | Integer | Estimated development effort in person-hours ($eff(r_j)$). |
| `Sat` | Float | Aggregated stakeholder satisfaction score ($sat(r_j)$). |

**Data Example (`RalicReqDataOpen.csv`):**
```csv
ReqID;Effort;Sat
a.1;805;321.0999776
a.1.1;354;0
a.1.2;27;14.321098
```

---

### Category D: Elicitation Datasets (`RalicReqStkData*.csv`)

* **Format:** Semicolon-separated values (`;`).
* **Structure:** Rows represent requirements (`ReqID`), and columns represent individual stakeholders, containing their granular preference values assigned during requirements prioritisation.

| Column | Type | Description |
| :--- | :--- | :--- |
| `ReqID` | String | Unique requirement identifier code. |
| `[Stakeholder_Name]` | Numeric | Preference score assigned by the stakeholder (Rank position, Rating scale 0–5/-1, or Points budget allocation). |

---

## Key Experimental Results Summary

1. **Stakeholder Pool Reduction:**
   * **OpenR:** Reduced from 127 candidates to 19 key stakeholders with AR (85.04% reduction) and 15 key stakeholders with HCR (88.19% reduction).
   * **ClosedR:** Reduced from 76 candidates to 23 key stakeholders for both AR and HCR (69.74% reduction).
2. **Conflict & Consensus Distance:**
   * OpenR exhibits moderate conflict, resulting in a measurable consensus distance between HCR and AR ($d_{Euclidean} = 0.0936$).
   * ClosedR exhibits high conflict ($3.14\times$ higher than OpenR), causing HCR to converge near AR ($d_{Euclidean} = 0.0298$).
3. **Impact on Prioritisation:**
   * Requirements prioritisation results are highly sensitive to the chosen preference elicitation technique (**Rank** is the most volatile, whereas **Rate** is more resilient).
   * Key stakeholder filtering significantly alters requirement priorities compared to unvetted crowd aggregation.

---


## License

This dataset and replication package are made available for academic, educational, and replication purposes.
