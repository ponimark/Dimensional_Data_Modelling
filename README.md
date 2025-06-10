# Actor & Player Seasons Data Pipelines

Welcome to the combined repository containing two robust SQL-based data pipeline projects designed to manage dimensionally modeled data for entertainment industry analytics. These projects implement Slowly Changing Dimensions (SCD) methodologies and Cumulative Table Design (CTD) to maintain historical data efficiently and support incremental updates.

---

## Project 1: Actor Films Data Pipeline

This project manages the **actor_films** table, which tracks actors, their films, and associated metrics like active status and average movie ratings by year.

### Key SQL Scripts

- **DIMENSIONAL_DATA_MODELLING.sql**  
  Backfills the `actor_films` table with data using a **Cumulative Table Design (CTD)** pattern. This establishes a comprehensive baseline dataset for further transformation.

- **SCD_TYPE2.sql**  
  Transforms the actor films data into a **Slowly Changing Dimension Type 2 (SCD Type 2)** design to enable historical tracking of changes while preserving prior states.

- **SCD_INCREMENTAL.sql**  
  Implements incremental updates to the `actor_films` table, processing only new or changed data since the last update to optimize performance.

- **actor_films_table.sql**  
  Defines the schema for the `actor_films` table, with key fields such as:  
  - `is_active` — Boolean flag indicating whether the actor is currently active.  
  - `avg_rating` — Average rating of each actor’s movies, calculated on a yearly basis.

### Workflow Summary

1. Populate the `actor_films` table via **DIMENSIONAL_DATA_MODELLING.sql** (CTD approach).  
2. Convert the table to SCD Type 2 format using **SCD_TYPE2.sql** to maintain historical data.  
3. Maintain the data with ongoing incremental updates from **SCD_INCREMENTAL.sql**.  
4. Review `actor_films_table.sql` for table structure and column details.

---
### 📂 Files – Actor-Film Project

| File Name                 | Description                                                                 |
|---------------------------|-----------------------------------------------------------------------------|
| `actor_films_table.sql`   | Base table for actor-year-movie data with `is_active` and `avg_rating`.     |
| `DIMENSIONAL_DATA_MODELLING.sql` | Builds a cumulative table with performance snapshots (CTD style).      |
| `SCD_TYPE2.sql`           | Converts CTD data into a Slowly Changing Dimension (Type 2).                |
| `SCD_INCREMENTAL.sql`     | Applies incremental updates simulating ETL loads.                           |




## Project 2: Player Seasons Data Pipeline

This parallel project manages data related to players and their season performances, leveraging similar dimensional modeling and SCD principles.

### Key SQL Scripts

- **Dimensional_Data_Modelling.sql**  
  Backfills the `player_season` table with comprehensive historical data using the **Cumulative Table Design (CTD)** methodology.

- **SCD_TYPE2.sql**  
  Converts `player_season` data into **SCD Type 2** format, enabling capture and tracking of historical changes over seasons.

- **SCD_TYPE2_INCREMENTAL_UPDATE.sql**  
  Facilitates incremental updates on the `player_season` table to efficiently append only new or modified records.

- **player_season_table.sql**  
  Defines the database schema for the `player_season` table, including fields such as:  
  - Player identifiers  
  - Season metrics and stats  
  - Flags and indicators to track active status and relevant performance attributes

### Workflow Summary

1. Initial population through **Dimensional_Data_Modelling.sql** using CTD principles.  
2. Historical versioning via **SCD_TYPE2.sql**.  
3. Incremental update application using **SCD_TYPE2_INCREMENTAL_UPDATE.sql**.  
4. Table structure and schema managed by **player_season_table.sql**.

---

## Combined Pipeline Highlights

- Both pipelines utilize **Cumulative Table Design (CTD)** to aggregate incremental data efficiently before applying SCD transformations.  
- The use of **Slowly Changing Dimension Type 2 (SCD Type 2)** enables robust historical data management, preserving full change history over time.  
- Incremental update scripts optimize processing by applying changes since the last run, reducing overhead and improving performance.  
- Tables **actor_films** and **player_season** hold domain-specific analytic data, including status flags, calculated averages, and time-sequenced records.

---
### 📂 Files – Player-Season Project

| File Name                          | Description                                                            |
|------------------------------------|------------------------------------------------------------------------|
| `player_season_table.sql`          | Contains player-season stats including rating, votes, and activity.    |
| `Dimensional_Data_Modelling.sql`  | Builds a cumulative player-season table with yearly snapshots.         |
| `SCD_TYPE2.sql`                    | Converts player data into Slowly Changing Dimension Type 2 format.     |
| `SCD_TYPE2_INCREMENTAL_UPDATE.sql`| Adds new records where player attributes have changed (incremental).   |



## Getting Started

1. Run the dimensional data modelling scripts (`DIMENSIONAL_DATA_MODELLING.sql` / `Dimensional_Data_Modelling.sql`) to backfill tables using CTD.
2. Execute the SCD Type 2 conversion scripts (`SCD_TYPE2.sql`) to enable historical tracking.
3. Use incremental update scripts (`SCD_INCREMENTAL.sql` / `SCD_TYPE2_INCREMENTAL_UPDATE.sql`) regularly to synchronize new data.
4. Refer to the respective table definition scripts to understand schema details.

## Additional Notes

- These pipelines are tailored for data warehousing environments that require historical tracking of dimension changes.
- The modular script design allows easy adaptation for other similar dimension tables and subject areas.
- Ensure execution order is followed to maintain data integrity and consistency.

Thank you for exploring these data modeling and SCD implementations. For questions, enhancements, or contributions, please open an issue or pull request.
