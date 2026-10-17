# 📊 Data Visualization Task — CodeAlpha Internship
## Nigerian E-Commerce Sales Dataset (2025)

**Analyst:** Abdulsobur Adebayo

**Tool:** Tableau 

**Dataset:** codealpha_task2_3_sales_eda_visualization.csv (1,500 rows)

**Deliverable:** Interactive dashboard + data story + portfolio-ready visuals

## 📑 Table of Contents

**Project Brief**
1. Data Preparation Before Visualization
2. Design Principles for These Visuals
3. Chart Plan (8 Core Visuals)
4. Step-by-Step Tableau Build Guide
5. Dashboard Layout & Story Flow
6. The Data Story (Narrative Script)
7. Portfolio Packaging for GitHub
8. Full Documentation Template

##1. Project Brief
The Data Visualization task asks for five things. Here's how each is addressed:

Task Requirement	How This Project Delivers
Transform raw data into visual formats	Clean CSV → Tableau Data Source → 8 core charts + 1 dashboard
Use Tableau for visuals	Full step-by-step Tableau build guide (with Power BI fallback)
Design visuals that enhance understanding	Enforced design system: color palette, typography, hierarchy
Craft compelling data stories	5-act narrative + executive summary for decision-makers
Build a portfolio	GitHub repo structure + README + screenshot deliverables
## 2. Data Preparation Before Visualization
2.1 Issues Carried Over from EDA
Before building any chart, fix these (in Tableau Prep, Power Query, or SQL):

Issue	Fix in Tableau
2 NULL region values	Replace with 'Unknown'
1 NULL quantity	Exclude row
Product names case-inconsistent (mouse, Mouse)	UPPER(TRIM([Product]))
sales_channel has trailing spaces	TRIM([Sales Channel])
Negative profit rows
