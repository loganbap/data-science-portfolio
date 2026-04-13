# Data Science Portfolio

> A curated collection of data science and analytics projects spanning machine learning, big data engineering, and data storytelling.

---

## About Me

I am a generalist data scientist and analyst with a passion for turning complex data into clear, compelling stories. My work spans the full data lifecycle from building large scale data pipelines to crafting visualizations that make insights accessible to any audience. I am eager to keep growing and learning, and I bring curiosity and collaboration to every project I work on.

**Core skills:** Python · R · PySpark · Apache Spark · Kafka · NiFi · Hive · HBase · Docker · Tableau · scikit-learn · pandas · SQL

---

## Featured Projects

| # | Project | Domain | Tools |
|---|---------|--------|-------|
| 1 | [Lottery Randomness & ROI Storytelling](#1-lottery-randomness--roi-storytelling) | Data Storytelling | Tableau |
| 2 | [Thoracic Surgery Survival Modeling](#2-thoracic-surgery-survival-modeling) | Medical / ML | R |
| 3 | [Movie Recommender System](#3-movie-recommender-system) | Recommender Systems | Python, scikit-learn |
| 4 | [TSA Complaints Stakeholder Story](#4-tsa-complaints-stakeholder-story) | Operational Analytics | PowerPoint, Visualization |
| 5 | [Childcare Cost & Affordability Analysis](#5-childcare-cost--affordability-analysis) | Policy Analysis | Python, Visualization |
| 6 | [Titanic Big-Data ML Pipeline](#6-titanic-big-data-ml-pipeline) | Data Engineering / ML | NiFi, Hive, Spark, HBase, Docker |
| 7 | [Capstone – Initial Analytics](#7-capstone--initial-analytics-placeholder) | Real-World Consulting | TBD |
| 8 | [Capstone – Modeling & Recommendations](#8-capstone--modeling--recommendations-placeholder) | Real-World Consulting | TBD |
| 9 | [Capstone – Final Presentation & Handoff](#9-capstone--final-presentation--handoff-placeholder) | Real-World Consulting | TBD |
| 10 | [Visual Storytelling Gallery](#10-visual-storytelling-gallery) | Data Visualization | Tableau, PowerPoint |

---

## Project Summaries

### 1. Lottery Randomness & ROI Storytelling
A multisheet Tableau story using several lottery CSV data sources to explain how drawings behave statistically across different U.S. games. Designed histograms, bubble charts, ROI distributions, and small multiples with annotations and parameters to debunk "hot number" and "lucky day" myths and show that typical player ROI is strongly negative.

**Focus:** Data storytelling and statistical communication | **Tools:** Tableau

---

### 2. Thoracic Surgery Survival Modeling
Fit a multivariate logistic regression model in R to predict 1-year mortality after thoracic surgery using clinical variables including diagnosis, tumor size, and comorbidities. Interpreted coefficients to surface clinically meaningful risk factors and achieved ~84.8% training accuracy.

**Focus:** Binary classification, interpretable medical risk modeling | **Tools:** R, glm

---

### 3. Movie Recommender System
Built a user based collaborative filtering system on the MovieLens small dataset (9,742 movies, 100,836 ratings, 610 users). Handled sparse ratings, computed user-user cosine similarity, and implemented an interactive function that produces top-10 personalized movie recommendations.

**Focus:** Recommender systems, similarity-based ML | **Tools:** Python, pandas, NumPy, scikit-learn

---

### 4. TSA Complaints Stakeholder Story
Analyzed TSA complaint trends to identify when and where airport screening issues were most acute. Designed a PowerPoint data story using heatmaps, spatial maps, line charts, and box plots framing findings around stakeholder decisions and benchmarking Charlotte Douglas (CLT) airport as a lower complaint example.

**Focus:** Exploratory analysis, operational storytelling | **Tools:** PowerPoint, heatmaps, spatial maps

---

### 5. Childcare Cost & Affordability Analysis
Analyzed county level childcare prices and affordability across the U.S. using over 3,000 county records. Quantified price to burden relationships, modeled a $2,000 annual subsidy scenario, and delivered findings as an executive summary, infographic, and social media ready visuals.

**Focus:** Policy analysis, scenario modeling, visual communication | **Tools:** Python, correlation analysis, infographics

---

### 6. Titanic Big-Data ML Pipeline
Built an E2E pipeline where Apache NiFi ingests a custom Titanic CSV into HDFS, Hive exposes the data as a managed table, and Spark ML trains a logistic regression classifier. Wrote model metrics to HBase, all running inside a Hadoop/Spark Docker cluster.

**Focus:** Big-data architecture, data engineering, ML integration | **Tools:** NiFi, HDFS, Hive, PySpark, HBase, Docker

---

### 7. Capstone – Initial Analytics *(placeholder)*
Ongoing real world capstone engagement. Covers problem framing, exploratory analysis, and initial visualizations connecting data signals to operational decisions for a client partner.

**Focus:** Stakeholder collaboration, problem framing, baseline analytics | **Tools:** TBD

---

### 8. Capstone – Modeling & Recommendations *(placeholder)*
Planned second capstone phase: predictive or explanatory models with clear feature importance explanations and practical recommendations for non-technical decision-makers.

**Focus:** E2E modeling, storytelling for non-technical audiences | **Tools:** TBD

---

### 9. Capstone – Final Presentation & Handoff *(placeholder)*
Final capstone phase: polished presentation, written report, and handoff materials the client can continue to use... integrating visual dashboards, key takeaways, and workflow documentation.

**Focus:** Professional communication, documentation, real-world impact | **Tools:** TBD

---

### 10. Visual Storytelling Gallery
A curated collection of standout individual visualizations and dashboards from across multiple projects: covering lottery probability, aviation complaints, and childcare policy. Demonstrates breadth of visualization and narrative technique in a compact format. Ideally, incorporate this into a resume link or QR code. 

**Focus:** Visualization breadth, narrative design | **Tools:** Tableau, PowerPoint

---

## Repository Structure

```
data-science-portfolio/
├── README.md                          # This file — portfolio cover page
├── projects/
│   ├── childcare-cost-affordability/
│   │   └── README.md
│   ├── titanic-bigdata-ml-pipeline/
│   │   └── README.md
│   └── ... (additional project folders)
└── archive/                           # Older or incomplete work
```

---

*Portfolio developed as part of an ongoing data science program. Updated continuously.*
