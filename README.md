

# Replication Package:  evidence-based stakeholder identification .....

This repository contains the replication datasets for the paper **"Evidence-based stakeholder identification and conflict management in a requirements prioritisation context"** by  José del Sagrado and Isabel M. del Águila  (Department of Informatics, University of Almería).


## Overview

The dataset provides the experimental data used to evaluate the proposed operationalization method for identifying stakeholder salience based on three core attributes: **Urgency (`urg`)**, **Legitimacy (`leg`)**, and **Power (`pow`)**. 

The source metrics are derived from the original RALIC project dataset, which is publicly available at [Sooling Lim's Dataset Repository](https://soolinglim.com/Datasets.html). To evaluate effectiveness in maintaining equality and diversity, the arrangement model is systematically evaluated by mapping these stakeholder attributes into **two and three intervals** per dimension, producing distinct stakeholder **subgroups**.


## Repository Structure

The repository includes the XX primary `.csv` files corresponding exactly to XXXX evaluated in the case study:

1. `stks_grouped_mid_points.csv`  


## Data Format & Schema

Each CSV file uses a semicolon (`;`) as a separator and follows this structure:

| Column | Type | Description |
| :--- | :--- | :--- |
| `class` | String | The assigned stakeholder salience subgroup combination (e.g., `"low.low.low"`, `"low.mod.high"`) based on interval mappings. |



### Data Example
```csv
"class";"key";".....
```


 
  - This dataset is made available for academic and replication purposes.
