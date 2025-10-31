# Analyzing UFC Fighters’ Physical Attributes and Fight Outcomes

## Overview
This term project investigates how UFC fighters’ **physical attributes** (height, reach, stance, age, etc.) and **technical performance metrics** (striking accuracy, defense, takedown ability) influence their fight outcomes.  
The analysis combines **fighter-level** and **fight-level** data, forming a comprehensive dataset that connects fighter characteristics with actual fight results.

Through this project, I aim to apply the full data science pipeline:  
data collection → cleaning → exploratory analysis → visualization → statistical modeling → interpretation of insights.

---

## Motivation
I have been personally involved in **boxing** and **kickboxing** for several years. Because of this, analyzing combat sports data excites me both personally and academically.  
Working on this project allows me to blend my passion for martial arts with my computer science and data science background.  
I believe that understanding what makes fighters successful — whether it’s reach, accuracy, or defense — can provide valuable insights not only for fans, but also for coaches and athletes themselves.

---

## Data Sources

### 1. `fighter_stats.csv`
**Source:** [UFC Complete Dataset (All Events 1996–2024)](https://www.kaggle.com/datasets/maksbasher/ufc-complete-dataset-all-events-1996-2024)  
**Description:** Contains aggregated fighter-level data describing the physical and performance statistics of UFC athletes.

| Column Name | Description |
|--------------|-------------|
| `name` | Fighter’s full name |
| `wins` | Total number of wins |
| `losses` | Total number of losses |
| `height` | Fighter’s height (in centimeters) |
| `weight` | Fighter’s weight (in kilograms) |
| `reach` | Arm reach (in centimeters) |
| `stance` | Preferred stance: Orthodox, Southpaw, Switch, etc. |
| `age` | Fighter’s age |
| `SLpM` | *Significant Strikes Landed per Minute* |
| `sig_str_acc` | *Significant Strike Accuracy* (ratio of landed to attempted strikes) |
| `SApM` | *Significant Strikes Absorbed per Minute* |
| `str_def` | *Strike Defense Rate* (percentage of strikes successfully avoided) |
| `td_avg` | *Takedowns Landed per 15 Minutes* |
| `td_acc` | *Takedown Accuracy* |
| `td_def` | *Takedown Defense* |
| `sub_avg` | *Average Submission Attempts per 15 Minutes* |

**Size:** 2,479 fighters × 16 columns  
**Purpose:** To provide fighter-level physical and skill attributes that can later be linked to actual fight outcomes.

---

### 2. `raw_fights.csv`
**Source:** [UFC Fights, Fighters, and Events Dataset](https://www.kaggle.com/datasets/aminealibi/ufc-fights-fighters-and-events-dataset)  
**Description:** Contains fight-level information for over 8,000 UFC bouts including participants, match results, and event data.

| Column Name | Description |
|--------------|-------------|
| `Fight_Id` | Unique fight identifier |
| `Win/No Contest/Draw` | Indicates the fight result outcome |
| `Fighter_1` | Name of the first fighter |
| `Fighter_2` | Name of the second fighter |
| `KD_1`, `KD_2` | Number of knockdowns landed by each fighter |
| `STR_1`, `STR_2` | Total significant strikes landed by each fighter |
| `TD_1`, `TD_2` | Takedowns landed by each fighter |
| `SUB_1`, `SUB_2` | Submission attempts by each fighter |
| `Weight_Class` | The weight division of the fight (e.g., Lightweight, Middleweight) |
| `Method` | How the fight ended (KO/TKO, Submission, Decision, etc.) |
| `Round` | The round in which the fight ended |
| `Fight_Time` | Time remaining or elapsed when the fight concluded |
| `Event_Id` | Unique identifier of the event the fight occurred in |

**Size:** 8,351 fights × 17 columns  
**Purpose:** Provides bout-level results and performance metrics, enabling correlation with fighter-level attributes.

---

## Enrichment Plan
The project guidelines require that any publicly available dataset must be **enriched by another dataset**.  
Here, enrichment occurs by **combining the fighter-level and fight-level data**:

- `raw_fights.csv` → represents *what happened* (fight outcomes).  
- `fighter_stats.csv` → represents *who fought* (fighter attributes).

By merging the two datasets using the fighter names, each fight will include detailed information about both fighters’ height, reach, stance, and performance metrics.

