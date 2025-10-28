# ==========================================
# Synthetic Browser Churn Dataset Generator
# Author: A.R.A Mirunalini
# Project: Chrome vs Edge User Analysis
# Date: 28-10-2025
# ==========================================

import numpy as np
import pandas as pd
import random

# ---------- 1. Basic Config ----------
np.random.seed(42)
n = 5000

# ---------- 2. Helper Functions ----------
def sigmoid(x):
    return 1 / (1 + np.exp(-x))

# ---------- 3. Define Base Features ----------

# Demographics
os_type = np.random.choice(["Windows", "macOS", "Linux"], size=n, p=[0.7, 0.2, 0.1])
region = np.random.choice(["North America", "Europe", "Asia", "Others"], size=n, p=[0.25, 0.25, 0.35, 0.15])
age_group = np.random.choice(["<25", "25-40", "40-60", "60+"], size=n, p=[0.3, 0.4, 0.2, 0.1])
default_search_engine = np.random.choice(["Bing", "Google", "DuckDuckGo"], size=n, p=[0.6, 0.3, 0.1])

# Engagement
daily_usage_time = np.random.normal(120, 50, n).clip(10, 300)
extensions_installed = np.random.poisson(3, n).clip(0, 15)
cross_device_sync = np.random.choice([0, 1], size=n, p=[0.4, 0.6])
homepage_customized = np.random.choice([0, 1], size=n, p=[0.5, 0.5])

# Experience
days_since_last_update = np.random.randint(0, 90, n)
avg_load_speed = np.random.normal(2.5, 0.8, n).clip(0.5, 5)
crash_count = np.random.poisson(2 + (days_since_last_update > 30).astype(int), n).clip(0, 10)

# Psychographics
privacy_concern_level = np.random.uniform(1, 10, n)
ad_block_usage = np.random.choice([0, 1], size=n, p=[0.5, 0.5])
feedback_submitted = np.random.choice([0, 1], size=n, p=[0.7, 0.3])

# ---------- 4. Derived Satisfaction ----------
# Base satisfaction inversely related to crashes and load speed
satisfaction_score = (
    10 
    - 0.7 * crash_count 
    - 0.8 * avg_load_speed 
    + 0.01 * daily_usage_time
)
# Add noise and clip range
satisfaction_score = satisfaction_score + np.random.normal(0, 1, n)
satisfaction_score = np.clip(satisfaction_score, 1, 10)

# ---------- 5. Compute Churn Probability ----------
# Weights (based on earlier discussion)
b = -3.0
w1, w2, w3, w4, w5, w6 = 0.8, 0.4, 0.6, 0.25, 0.6, 0.15

churn_score = (
    b
    + w1 * (10 - satisfaction_score)
    + w2 * crash_count
    + w3 * avg_load_speed
    + w4 * privacy_concern_level
    - w5 * (daily_usage_time / 100)
    - w6 * extensions_installed
)

p_churn = sigmoid(churn_score)

# ---------- 6. Add Logical Adjustments ----------
# Privacy-conscious with no adblock
p_churn += 0.1 * ((privacy_concern_level > 7) & (ad_block_usage == 0))
# Loyal Windows users
p_churn -= 0.05 * (os_type == "Windows")
# Google searchers slightly higher churn
p_churn += 0.05 * (default_search_engine == "Google")
# Strongly engaged users stay
p_churn -= 0.1 * ((daily_usage_time > 200) & (extensions_installed > 5))
# Cross-device sync lowers churn
p_churn -= 0.05 * (cross_device_sync == 1)

# Clip between [0,1]
p_churn = np.clip(p_churn, 0, 1)

# ---------- 7. Generate Final Churn Labels ----------
churn = np.random.binomial(1, p_churn)

# ---------- 8. Assemble DataFrame ----------
df = pd.DataFrame({
    "user_id": np.arange(1, n+1),
    "daily_usage_time": daily_usage_time,
    "avg_load_speed": avg_load_speed,
    "crash_count": crash_count,
    "ad_block_usage": ad_block_usage,
    "extensions_installed": extensions_installed,
    "satisfaction_score": satisfaction_score,
    "privacy_concern_level": privacy_concern_level,
    "os_type": os_type,
    "region": region,
    "age_group": age_group,
    "default_search_engine": default_search_engine,
    "cross_device_sync": cross_device_sync,
    "homepage_customized": homepage_customized,
    "days_since_last_update": days_since_last_update,
    "feedback_submitted": feedback_submitted,
    "churn": churn
})

# ---------- 9. Sanity Checks ----------
print(df.head())
print("\nDataset shape:", df.shape)
print("Churn rate: {:.2f}%".format(df['churn'].mean() * 100))

# ---------- 10. Save Dataset ----------
df.to_csv("browser_churn_data.csv", index=False)
print("\n Dataset saved as browser_churn_data.csv")


print("\nCorrelation with churn:\n", df.corr(numeric_only=True)["churn"].sort_values(ascending=False))
