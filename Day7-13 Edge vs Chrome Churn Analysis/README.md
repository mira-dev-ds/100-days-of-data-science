Browser Churn Data Generation

This project simulates real-world user behavior for Microsoft Edge users, focusing on identifying patterns that lead to browser churn — users switching from Edge to Chrome. The dataset is designed to support churn analysis, EDA, and machine learning experiments.

🎯 Objective

The goal of this project is to generate a realistic synthetic dataset that reflects how users interact with a web browser and what behavioral patterns influence their likelihood to switch.

🧩 Features Included
Feature	Type	Description
user_id	Integer	Unique user identifier
age	Integer	User’s age (18–70)
region	Categorical	User’s region (e.g., North America, Europe, Asia)
device_type	Categorical	Device used — Desktop, Laptop, or Mobile
daily_usage_time	Float	Average daily usage time in minutes
avg_load_speed	Float	Average page load speed (in seconds)
crash_count	Integer	Number of browser crashes per week
extensions_installed	Integer	Number of browser extensions installed
ad_block_usage	Binary	1 if ad blocker is used, else 0
privacy_concern_level	Integer	User’s privacy concern (1–10)
satisfaction_score	Float	User satisfaction level (1–10)
frequency_of_updates	Integer	Number of updates per month
technical_literacy	Integer	Technical skill level (1–10)
ad_exposure_score	Float	Exposure to ads (1–10)
churn	Binary	1 = switched to Chrome, 0 = stayed on Edge
⚙️ Logic Behind the Data

This dataset is not random. Logical relationships are embedded to mimic real-world behavior:

Higher crash_count, slower load_speed, and lower satisfaction increase churn probability.

Strong privacy concerns combined with stable performance reduce churn.

Users with high ad exposure or frequent crashes are more likely to switch.

These relationships ensure realistic correlations and non-linear patterns — ideal for churn prediction modeling.

🧠 Tech Stack

Python 3.x

pandas, numpy, random, matplotlib (for verification and visualization)

🚀 How to Run

Clone this repository or download the script file.

Install dependencies:

pip install pandas numpy matplotlib


Run the script:

python generate_browser_churn_data.py

The dataset will be saved as:

browser_churn_data.csv
The dataset will be saved as:

browser_churn_data.csv
