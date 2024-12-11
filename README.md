Men's IPL T20 Dashboard: Player Performance Analysis to create your own team of 11 players

### 📊 Power BI Dashboard for IPL T20 Performance Insights

This project uses Power BI to analyze IPL T20 player performances, enabling the selection of the best XI players for a team. By categorizing players into **power hitters**, **middle-order batsmen**, **lower-order anchor**, **all-rounders**, and **specialist bowlers**, the dashboard helps create a balanced and strategic lineup.

---

## 🔍 **Project Overview**

### Problem Statement:
Task: Create a team of best 11 cricket players

Requirement: 
1. Team should be able to score at least 180 on an average
2. Team should be  able to defend 150 runs on an average
3. Margin of runs to play with = 30

Parameters:

<img width="628" alt="Untitled (36)" src="https://github.com/user-attachments/assets/5c747751-8ab0-48b6-bf6c-01da7c82d987">
<img width="607" alt="Untitled (37)" src="https://github.com/user-attachments/assets/eff957cd-a3e1-4dae-9c09-93221b92e0a1">
<img width="611" alt="Untitled (38)" src="https://github.com/user-attachments/assets/27f33555-bcae-49f1-a533-7328fdf55daa">
<img width="606" alt="Untitled (39)" src="https://github.com/user-attachments/assets/bcab7d84-9240-46b7-990a-a2402e9299e1">
<img width="615" alt="Untitled (40)" src="https://github.com/user-attachments/assets/2015c7a6-0189-4b2e-88a7-0039e964e7cc">


To create an interactive dashboard that:
- Analyzes batting, bowling, and all-rounder performances.
- Select the best 11 players based on their roles.
- Form a strategic batting order (Power Hitters ➡️ Middle Order ➡️ Lower Order ➡️ All-rounders ➡️ Specialist Bowlers).

### Features:
- Performance analysis of players across all IPL matches in 2022.
- Player rankings by batting strike rate, economy rate, average, and overall impact.
- Visuals showcasing team and player insights, enabling informed decision-making.

---

## 📂 **Data Sources**
The data is extracted from [ESPNcricinfo](https://www.espncricinfo.com/) and includes:
1. **`dim_match_summary.csv`**: Match details.
2. **`dim_players.csv`**: Player profiles and attributes.
3. **`fact_bating_summary.csv`**: Batting performance statistics.
4. **`fact_bowling_summary.csv`**: Bbowling performance statistics.

---

## Step 1: Scraped data using a data collector(web-crawler) by Bright Data
### Tables scraped

1. Match results
<img width="478" alt="{F5B2D8B4-29B2-464A-AD5E-08F974BEFF27} (1)" src="https://github.com/user-attachments/assets/0dee6492-823e-4413-9ad4-dba95642d23f">


2. Batting scorecards
<img width="447" alt="{A67622C9-9136-41B6-BE28-041DB436C27D}" src="https://github.com/user-attachments/assets/d9122e8d-0f35-4672-9d5a-a140e9a75246">


3. Bowling scorecards
<img width="451" alt="{C671CF34-71B0-4375-99EE-A5FC7E234B2F} (1)" src="https://github.com/user-attachments/assets/ea3714ac-287e-4936-8743-99016f3cdc5d">


4. Detailed players information
<img width="394" alt="{523B369B-8B92-4AE3-9EEE-C7D8C43C5ACE} (1)" src="https://github.com/user-attachments/assets/e5016d6f-91b5-48d6-b9a9-024f44286d50">

## Step 2: Data preprocessing using Pandas

1. Match results
- transformed from JSON to  pandas df
- renamed scorecard to match id. Will use to link other tables (in Power BI)
<img width="73" alt="{992DF462-7178-4809-AE03-5B05A0296E31}" src="https://github.com/user-attachments/assets/a36a3e2b-3228-4106-84d6-87d37a575b2b">

2. Processing t20_wc_batting_summary
- Created out/not out column from dismissal using the LAMBDA function.
- Deleted dismissal column
<img width="377" alt="{C80FADCF-9608-4C64-A6C5-6F84820FB289}" src="https://github.com/user-attachments/assets/1b554fee-a3b6-47b5-b819-7d553ff8640a">
- removed special characters from batsmanName

**Created a dictionary which acts like a link between all the tables using match_id. This maps team names to a unique id.**

## Step 3: Data transformation in Power Query

- corrected data types
- removed extra spaces, characters
- created a conditional column to separate Qualifier matches from Super 12
<img width="662" alt="{D9491570-49DA-4593-A321-A65FD248AD42}" src="https://github.com/user-attachments/assets/89c782a8-0c8e-4549-904f-401a28868d43">

- renamed columns for convenience
- removed duplicates
- split overs column in two. 2.5 overs to 2 over 5 balls. then created ‘balls faced’ custom column; a sum of both.
- converted out/not_out to binary 1/0 respectively

## Step 4: Data Modeling

Star schema
dimension tables: dim_players, dim_match_summary
fact tables: fact_batting_summary, fact_bowling_summary
<img width="587" alt="{645EF57B-C389-46AE-944D-947ED27560A8}" src="https://github.com/user-attachments/assets/0a860bb9-eef9-4502-b44b-15bf5237b02a">

## Step 5: Building DAX measures and calculated columns

All measures stored in the folder ‘Key Measures’ under their respective sub-folders.
**DAX measures count**

- fact_batting_summary: 9
- fact_bowling_summary: 8
- others: 3

**Calculated columns count**

- fact_batting_summary: 1
- fact_bowling_summary: 1
- dim_player: 1

*Excel file provided*
## 🚀 **Dashboard Highlights**

## Step 6: Dashboard mockup

**digital design provided ‘mockup.txt.’**
![dashboard mockup](https://github.com/user-attachments/assets/4f094c0b-113a-460f-867f-4f89ec55c055)

---

## 🛠️ **Technical Details**
- **Tool Used**: Power BI
- **Programming**: No coding; data transformations and visualizations are handled within Power BI.
- **Data Cleaning**: Preprocessed to ensure accuracy and consistency.

---

## 📋 **How to Use This Repository**

1. **Download the Repository**:
   Clone or download the repository to your local system.

   ```bash
   git clone https://github.com/DjangoMustang/IPL-T20-Dashboard.git
   ```

2. **Setup Instructions**:
   - Ensure Power BI Desktop is installed.
   - Load the `.csv` files provided in the repository into Power BI.

3. **Open the Dashboard**:
   Import the `.pbix` file into Power BI Desktop to explore the dashboard.

4. **Customize**:
   Use slicers and filters to explore data by season, team, or individual players.

---

## 🖼️ **Dashboard Preview**

<img width="668" alt="{A3637769-D16C-4C07-B7FF-321125F9A3DC}" src="https://github.com/user-attachments/assets/573a6632-49c2-4eb5-8323-d9b852082e37">
<img width="671" alt="{3C078D6E-183F-4A02-B961-99BCE240D094}" src="https://github.com/user-attachments/assets/b5df5b7d-3327-4afb-8808-ff89ec7c78d6">
<img width="667" alt="{365486B0-9DD5-4456-88B0-46AA692CBBF7}" src="https://github.com/user-attachments/assets/1356f20c-674a-4f73-9f6f-5d3297d60778">
<img width="668" alt="{74501BFB-1C53-4908-9536-ACCDFFCB9655}" src="https://github.com/user-attachments/assets/d716473b-04d9-49e0-aacd-33c4a95559da">
<img width="668" alt="{5CCF256B-A559-4DA3-ADA9-5EB173894BE2}" src="https://github.com/user-attachments/assets/1ac1eff6-da13-44b9-9a71-33e9fbabaf79">
<img width="668" alt="{8C867A10-AEFF-4D5C-8ED2-A3EBF833A514}" src="https://github.com/user-attachments/assets/6111c151-ec74-4595-8920-abc19b3d51b8">


---

## 🤝 **Contributions**
Contributions, issues, and feature requests are welcome. Feel free to check the [issues page](https://github.com/YourUsername/IPL-T20-Dashboard/issues).

---

## 📝 **License**
This project is licensed under the MIT License.

---

## 📧 **Contact**
For queries or feedback, feel free to contact:
- **Siddhi Shrivastava**
- **Email**: [siddhi.atwork@gmail.com](mailto:siddhi.atworkl@gmail.com)
- **GitHub**: [DjangoMustang](https://github.com/DjangoMustang)
- **Instagram**: ([thats_siddhi](https://www.instagram.com/thats_siddhi))

---

## **Creadits**
Problem statement is defined by Codebasics Resume Project Challenge. I built the dashboard from scratch but continued with their dashboard mockup design, it's the best.
Huge thanks to the whole team of Codebasics!!!
