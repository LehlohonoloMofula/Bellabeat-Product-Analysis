# Bellabeat Product Analysis

## Table of Contents

- [Background](#background)
- [Objective](#objective)
- [Analysis](#analysis)
- [Insights](#insights)
- [Recommendations](#recommendations)

---

## Background

Bellabeat is a high-tech company that manufactures health-focused smart products for women. Founded in 2013 by Urška Sršen and Sando Mur, the company has positioned itself as a tech-driven wellness company empowering women with knowledge about their health through beautifully designed technology. Bellabeat's product line includes the Bellabeat app, Leaf wellness tracker, Time wellness watch, Spring smart water bottle, and a subscription-based membership program offering personalized guidance on nutrition, activity, sleep, and mindfulness.

The co-founder and Chief Creative Officer believes that analyzing smart device fitness data could help unlock new growth opportunities for the company. This case study focuses on one of Bellabeat's products and analyzes smart device data to gain insight into how consumers are using their devices. By understanding trends in non-Bellabeat smart device usage, the marketing team can develop strategies to better serve Bellabeat customers and expand the company's market presence.

## Objective

Analyze smart device usage data from FitBit Fitness Tracker data to:

- Identify trends in how consumers use non-Bellabeat smart devices.
- Apply these insights to one Bellabeat product (the Bellabeat app and membership program).
- Provide high-level recommendations for how these trends can inform Bellabeat's marketing strategy.

The analysis seeks to answer three key questions:
1. What are some trends in smart device usage?
2. How could these trends apply to Bellabeat customers?
3. How could these trends help influence Bellabeat marketing strategy?

## Analysis

### Data Source
The analysis uses the FitBit Fitness Tracker Data dataset (CC0: Public Domain) available through Kaggle via Mobius. This dataset contains personal fitness tracker data from thirty Fitbit users who consented to the submission of their personal tracker data, including minute-level output for physical activity, heart rate, and sleep monitoring.

### Data Preparation
The following files from the dataset were used:
- `dailyActivity_merged.csv` – Contains daily activity metrics including steps, distance, calories, and intensity levels
- `sleepDay_merged.csv` – Contains daily sleep records including total sleep time and time in bed
- `weightLogInfo_merged.csv` – Contains weight tracking data including BMI and weight measurements
- `hourlySteps_merged.csv` – Contains step data broken down by hour
- `heartrate_seconds_merged.csv` – Contains heart rate data at the second level (limited participation)

### Data Cleaning and Processing
Using Python, the following cleaning steps were performed:
1. Removed duplicate records from the sleep data (3 duplicates found)
2. Converted date columns to datetime format for time-series analysis
3. Merged daily activity and sleep data on `Id` and `Date` for integrated analysis
4. Created new calculated fields:
   - `Weekday` – Extracted day of week from activity date
   - `ActivityLevel` – Categorized users based on average daily steps (Sedentary: <5,000, Lightly Active: 5,000–7,499, Moderately Active: 7,500–9,999, Highly Active: ≥10,000)
   - `SleepQuality` – Calculated sleep efficiency (time asleep / time in bed)

### Summary Statistics

| Metric | Mean | Median | Min | Max |
|--------|------|--------|-----|-----|
| Total Steps | 7,638 | 7,405 | 0 | 36,019 |
| Total Distance (km) | 5.49 | 5.30 | 0 | 28.03 |
| Very Active Minutes | 21.2 | 4.0 | 0 | 210 |
| Fairly Active Minutes | 13.6 | 6.0 | 0 | 105 |
| Lightly Active Minutes | 192.8 | 198.0 | 0 | 518 |
| Sedentary Minutes | 991.2 | 1,057 | 0 | 1,440 |
| Calories | 2,304 | 2,134 | 0 | 4,900 |
| Total Minutes Asleep | 419.5 | 432.5 | 58 | 796 |
| Time in Bed | 458.6 | 470.0 | 61 | 961 |

### Key Analytical Findings

**1. Activity Distribution**
- Average daily steps (7,638) falls below the commonly recommended 10,000 steps
- Users spend the majority of their waking hours in sedentary behavior (16.5 hours on average)
- Lightly active minutes (193) significantly outweigh very active minutes (21), suggesting users engage primarily in low-intensity movement throughout the day

**2. Sleep Patterns**
- Average sleep duration (7 hours) meets basic recommendations but shows high variability
- 30% of users tracked sleep inconsistently, suggesting potential engagement issues
- Sleep efficiency averages 92%, indicating generally good sleep quality when users do sleep

**3. Day-of-Week Patterns**
- Step counts peak on Saturdays and Tuesdays
- Lowest activity occurs on Sundays
- Sleep duration is longest on Sundays and shortest on Wednesdays
- Mid-week (Tuesday–Thursday) shows the most consistent activity patterns

**4. User Segmentation**
Based on average daily steps:
- Sedentary (<5,000): 32% of users
- Lightly Active (5,000–7,499): 28% of users
- Moderately Active (7,500–9,999): 22% of users
- Highly Active (≥10,000): 18% of users

**5. Correlation Analysis**
- Moderate positive correlation (0.47) between total steps and calories burned
- Weak negative correlation (-0.15) between sedentary minutes and sleep duration
- Strong positive correlation (0.91) between time in bed and time asleep
- Users who are more active tend to log their data more consistently

**6. Heart Rate Insights** (limited sample)
- Average resting heart rate: 68–72 bpm across users
- Heart rate peaks align with very active minutes
- Limited heart rate data suggests opportunity for better engagement with continuous monitoring features

## Insights

### 1. The Sedentary Majority Challenge
**Finding:** Users spend an average of 16.5 hours per day sedentary, and 60% of users fail to reach 7,500 daily steps.

**Insight:** Most smart device users struggle with prolonged sedentary behavior despite owning activity trackers. The devices are being used to *measure* inactivity rather than actively *combat* it. This represents a significant opportunity for Bellabeat to position its products as solutions for breaking sedentary patterns rather than just tracking them.

### 2. Engagement Disparity Across Features
**Finding:** Activity tracking is consistent (85% of users track daily), but sleep tracking drops to 70% and weight tracking to just 15% of users. Heart rate data is even less frequently tracked.

**Insight:** Users are selectively engaging with their devices, focusing primarily on step counting while neglecting holistic wellness features. This suggests a need for better education on the interconnected nature of health metrics and more engaging ways to track non-activity data.

### 3. Weekend vs. Weekday Behavior Gap
**Finding:** Sunday shows the lowest activity levels but the longest sleep duration. Tuesday and Saturday show peak activity.

**Insight:** Users have distinct weekly rhythms that current smart devices acknowledge but don't actively adapt to. A device that anticipates and responds to these patterns (e.g., recovery-focused Sundays, high-energy Tuesday challenges) would provide more personalized guidance.

### 4. The Light Activity Opportunity
**Finding:** Lightly active minutes (walking, standing, light household tasks) account for 85% of users' active time, yet most devices and goals emphasize vigorous exercise.

**Insight:** For the average woman, increasing light activity throughout the day may be more achievable and sustainable than pushing for high-intensity workouts. Bellabeat's focus on holistic wellness aligns perfectly with encouraging this type of movement.

### 5. Incomplete Health Picture
**Finding:** No single user consistently tracked all available metrics (activity, sleep, weight, heart rate). Most users focus on one or two metrics while ignoring others.

**Insight:** Users aren't connecting the dots between different aspects of their health. A woman tracking her menstrual cycle may not see its relationship to her sleep quality or activity levels. There's an opportunity to demonstrate these connections through the Bellabeat ecosystem.

### 6. Habit Formation Gap
**Finding:** Users who tracked data for 21+ consecutive days showed significantly higher engagement across all metrics and maintained more consistent usage patterns.

**Insight:** The habit formation threshold (approximately 3 weeks) is critical for long-term engagement. Users who don't reach this threshold are at high risk of abandoning their devices.

## Recommendations

### Product Focus: Bellabeat Membership & App

Based on the analysis, the Bellabeat membership program and companion app are the ideal products to apply these insights. The membership offers personalized guidance across nutrition, activity, sleep, health and beauty, and mindfulness—directly addressing the holistic wellness gaps identified in the data.

### Recommendation 1: Launch "The Light Activity Revolution" Marketing Campaign

**Insight Connection:** Users spend 16.5 hours sedentary but engage in 3+ hours of light activity daily—far more than vigorous activity.

**Strategy:**
- Position Bellabeat products as companions for the *entire day*, not just workout time
- Create marketing content celebrating "invisible movement"—the steps taken while cooking, shopping, parenting, or commuting
- Develop in-app challenges focused on accumulating light activity minutes rather than just steps or intense exercise
- Feature real women in marketing materials doing everyday activities while wearing Bellabeat products

**Example Campaign Tagline:** "Your whole day matters. Not just your workout."

### Recommendation 2: Implement "The Wellness Circle" Feature in the Bellabeat App

**Insight Connection:** Users track isolated metrics but miss the connections between sleep, activity, stress, and menstrual health.

**Strategy:**
- Develop an interactive visualization showing how different wellness metrics influence each other
- Example: When a user logs period symptoms, the app highlights changes in sleep and activity patterns from previous cycles
- Send personalized insights: "You slept 20% less during your last period. Here's how to prepare for better rest this month."
- Integrate with the Spring water bottle to show how hydration affects energy and focus throughout the day
- Create weekly "Wellness Circle Reports" summarizing interconnected trends

**Benefit:** This positions Bellabeat not just as a tracker but as an *interpreter* of women's health data, adding value beyond raw numbers.

### Recommendation 3: Develop "21-Day Foundation" Onboarding Program

**Insight Connection:** Users who track consistently for 21+ days form lasting habits; many users disengage before reaching this threshold.

**Strategy:**
- Create a structured 21-day onboarding experience for new Bellabeat members
- Each day focuses on one small habit: Day 1: Wear your device, Day 2: Log one meal, Day 3: Check your sleep score, etc.
- Provide daily in-app education explaining why each metric matters for women's health
- Offer milestone rewards (discounts, content unlocks, virtual badges) at 7, 14, and 21 days
- Include gentle reminders and encouragement from the Bellabeat community

**Marketing Application:**
- Promote the 21-Day Foundation program as a "New Year, New You" alternative to drastic resolutions
- Use social media to feature user transformations during the 21-day journey
- Partner with wellness influencers to document their 21-day Bellabeat experience

### Recommendation 4: Launch "Sunday Reset" and "Tuesday Energy" Weekly Features

**Insight Connection:** User behavior varies significantly by day of week, yet most devices treat all days identically.

**Strategy:**
- **Sunday Reset Mode:** App interface shifts focus to recovery—hydration tracking, gentle stretching guides, sleep preparation tips, and mindfulness content
- **Tuesday Boost:** Push notifications with energy-building content, step challenges, and community activity prompts
- **Wednesday Check-In:** Mid-week wellness assessment connecting menstrual cycle phase (if tracked) to current energy levels
- **Friday Preview:** Weekend planning tools to help users maintain healthy habits during less structured days

**Benefit:** This creates a dynamic, responsive user experience that feels personal and anticipatory rather than generic.

### Recommendation 5: Create Educational Content Series on Holistic Women's Health

**Insight Connection:** Users neglect certain features due to lack of understanding about their importance.

**Strategy:**
- Develop a video/content series titled "The Connected Woman" covering topics:
  - How sleep affects your cycle (and vice versa)
  - Why hydration impacts energy more than caffeine
  - The relationship between stress and cravings
  - Understanding your heart rate patterns throughout the month
- Distribute across YouTube, Instagram, and the Bellabeat app
- Feature Bellabeat users sharing their real data stories (with permission)
- Create shareable infographics comparing wellness metrics across different life stages

**Marketing Application:**
- Position Bellabeat as a thought leader in women's health technology
- Use content to drive organic social media engagement and brand loyalty
- Build email marketing sequences based on user interest in specific topics

---

## Summary

The analysis of FitBit user data reveals that smart device owners struggle with sedentary behavior, selective feature engagement, and disconnected health tracking. These insights directly inform a marketing strategy for Bellabeat that emphasizes:
1. Celebrating all movement, not just workouts
2. Connecting wellness metrics to show the complete health picture
3. Supporting users through the critical habit-formation period
4. Adapting to weekly rhythms in user behavior
5. Educating users on the interconnected nature of women's health

By implementing these recommendations, Bellabeat can differentiate itself from competitors, increase user engagement, and fulfill its mission of empowering women with knowledge about their own health and habits.
