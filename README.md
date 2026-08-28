# GTA V Worldwide Sales & Performance Intelligence
A Tableau business intelligence project designed to analyze global sales performance, platform distributions, and revenue drivers for Grand Theft Auto V. The project transforms a comprehensive worldwide sales dataset into a star-schema relational model to serve as an operational benchmark for Rockstar Games as they evaluate legacy lifecycle trends and establish strategic performance baselines for the release of Grand Theft Auto VI.

## Table of Contents
- [Overview](#overview)
- [Problem Statement and Project Objectives](#Problem-Statement-and-Project-Objectives)
- [Data Pipeline and Architecture](#Data-Pipeline-and-Architecture)
- [Data Transformation and Cleaning](#Data-Transformation-and-Cleaning)
- [Data Model and Relationships](#Data-Model-and-Relationships)
- [Tableau Calculations and Business Logic](#Tableau-Calculations-and-Business-Logic)
- [Dashboards and Visualizations](#Dashboards-and-Visualizations)
- [Key Business Insights](#Key-Business-Insights)
- [Strategic Recommendations](#Strategic-Recommendations)
- [Tech Stack](#Tech-Stack)

## Overview
With Grand Theft Auto V spanning multiple console generations, digital shifts, and evolving monetization models (Downloadable Content and game sales), understanding its full lifecycle performance is crucial. This project constructs an analytics solution in Tableau, converting a monolithic flat-file dataset of worldwide sales metrics into a structured star-schema data warehouse. The interactive model allows stakeholders to evaluate regional revenue streams, platform adoption rates and release phase impacts.

## Problem Statement and Project Objectives
### Problem Statement
With Rockstar Games preparing for the commercial launch of Grand Theft Auto VI, leadership needed a comprehensive evaluation of Grand Theft Auto V's performance across its lifecycle spanning more than a decade. Without a centralized baseline comparing regional sales channels, platform generations, DLC revenue drivers, and promotional impacts, executive teams lack empirical benchmarks to set realistic revenue targets, optimize regional distribution strategies, and model player engagement metrics for GTA VI.

### Project Objectives
- Lifecycle Revenue Benchmarking: Analyze cumulative financial performance (Revenue and Downloadable Content Revenue) across release phases and game editions.
- Platform Analysis: Evaluate sales adoption and engagement trends across gaming platforms.
- Geographic & Regional Performance: Map revenue distributions, market sizes, and local adoption rates (country and region) to identify top-performing global markets.
- Channel Dynamics: Monitor sales channels and retailers alongside promotional events.

## Data Pipeline and Architecture
[Raw Dataset] ➔ [Power Query ETL] ➔ [Star Schema Data Model] ➔ [Calculated Fields & Parameters] ➔ [Interactive Tableau Workbook]

## Data Transformation and Cleaning
To transform the raw gta_v_worldwide_sales dataset into a star-schema model, ETL transformations were executed in Excel using PowerQuery prior to building relationships in Tableau Desktop's Logical layer:

- Creating Data Model: Split the dense flat file containing all the data into a central fact table and 7 lookup dimension tables.
- Surrogate Key Assignment: Generated primary key IDs (location_id, platform_id, game_edition_id, retailer_id, sales_channel_id, release_phase_id, special_event_id) using Index, across lookup tables to enable clean one-to-many relationships with the fact table.
- Field Standardization & Cleansing: Converted country codes into standardized full country names.

## Data Model and Relationships
The transformed data architecture follows a Star Schema centered around the transactional table (fact table) connected via standard one-to-many (1:*) dimensional joins:
<img width="1094" height="485" alt="Tableau DM" src="https://github.com/user-attachments/assets/d00dd89c-3dfc-4bc7-9ef8-decf11986acc" />

- fact table: Central fact table containing core transactional measures and metrics (gross_revenue_usd, dlc_revenue_usd, units_sold, average_selling_price_usd, discount_percentage, holiday_season, Date).
- dim_location: Geographic lookup table containing geographic hierarchies (location_id, country, country_code, region).
- dim_platform: Hardware breakdown lookup table (platform_id, platform).
- dim_game_edition: Game version lookup table (game_edition_id, game_edition).
- dim_release_phase: Lifecycle stage lookup table (release_phase_id, release_phase).
- dim_retailer: Distribution partner lookup table (retailer_id, retailer).
- dim_sales_channel: Channel classification lookup table (sales_channel_id, sales_channel).
- dim_special_event: Promotional campaign directory (special_event_id, special_event).

## Tableau Calculations and Business Logic
<img width="561" height="657" alt="Metric Parameter" src="https://github.com/user-attachments/assets/9d940401-6ce8-43e2-8269-c9dba3832f9a" />

<img width="555" height="652" alt="Year Parameter" src="https://github.com/user-attachments/assets/9b6ac54e-2df7-4e41-8582-63174b697030" />

<img width="732" height="429" alt="Revenue CY" src="https://github.com/user-attachments/assets/72978cbb-4dda-45be-981d-409bafb99322" />

<img width="728" height="427" alt="Revenue PY" src="https://github.com/user-attachments/assets/bde1768d-fc13-4e6c-b95f-db39815d6556" />

<img width="731" height="429" alt="YoY Revenue" src="https://github.com/user-attachments/assets/a199c65c-8dde-41b8-957e-f276337f30ad" />

<img width="731" height="430" alt="Metric CY" src="https://github.com/user-attachments/assets/b131e9ec-8339-481f-8178-8d680c64761d" />

<img width="731" height="430" alt="CY Label" src="https://github.com/user-attachments/assets/7f1e5ea2-6c9c-4ddd-954c-32e0a3fb5981" />

<img width="731" height="431" alt="Metric PY" src="https://github.com/user-attachments/assets/0771771a-b5e5-4433-b07a-2727bb091529" />

<img width="731" height="428" alt="PY Label" src="https://github.com/user-attachments/assets/45c9792e-1c53-4c05-be39-1da74f67d982" />

<img width="732" height="429" alt="Metric YoY" src="https://github.com/user-attachments/assets/b89696bb-ab88-4ac8-9ce0-f23466766bda" />

## Tech Stack
- Data Prep & ETL: Power Query Excel
- Data Modeling: Tableau Data Logical Layer 
- Calculations & Analytics: Tableau Calculated Fields
- Visualization: Tableau Desktop
