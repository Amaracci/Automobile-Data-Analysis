# Automobile-Data-Analysis
This project explores an automobile dataset to uncover factors that may influence insurance risk. The focus was on understanding how attributes like symboling, normalized losses, horsepower, and body style relate to each other and affect insurance perception and cost.

## Step 1: Data Cleaning
I began by loading the dataset and doing some basic sanity checks using data.info() and data.duplicated().sum() to confirm the structure and look for redundancy.

Several columns had missing values. Instead of dropping them, I filled them using the median, which is more robust to outliers:

- For numerical columns like price, horsepower, stroke, etc., I used the overall median.
- For normalized losses, I filled missing values using the median within each body-style group. This local median provides better context than the global one.
- I also converted number-of-doors to integers after filling, to ensure proper datatype.

This step ensured I didn't lose valuable data due to nulls and helped maintain dataset integrity.

## Step 2: Understanding Variable Distributions
Using histograms, I analyzed the distribution of key variables:
- Price: Right-skewed → Most cars are budget to mid-range, with a few luxury cars pulling the average up.
- Horsepower: Right-skewed → Most cars are moderately powered; high-performance cars are less common.
- Normalized Losses: Right-skewed → A few vehicles are linked to very high insurance losses.
- Symboling: Slightly right-skewed → Indicates most vehicles have average insurance risk, with some considered high risk.

These patterns helped frame the data landscape — most entries are centered around typical, mid-tier vehicles with fewer extremes.

## Step 3: Exploring Relationships (Regplots)
I used regression plots to visually examine how variables relate:

- Normalized Losses vs Symboling: Strong positive correlation, which means cars seen as higher risk by insurance (symboling) tend to have higher actual insurance losses.
- Normalized Losses vs Price: Positive correlation, which means higher-priced vehicles tend to have more insurance losses, possibly because of repair costs.
- Normalized Losses vs Engine Size & Horsepower: Weak to moderate positive correlation, which means more powerful cars may lead to higher losses.
- Symboling vs Number of Doors: Negative correlation, which means sportier, riskier cars (higher symboling) tend to have fewer doors.
- Normalized Losses vs Highway MPG: Weak negative correlation, which means more fuel-efficient cars may be slightly less risky.

Each plot helped build a picture of what insurance risk might look like through various features.

## Step 4: Grouped Insights
I grouped by make and body-style to see brand/body trends in symboling (insurance risk perception).
- By Make: Porsche, Saab, and Alfa-Romeo ranked highest, perceived as higher risk. Volvo had the lowest risk perception.
- By Body Style: Convertibles had the highest average symboling, suggesting they’re seen as sportier and riskier. Wagons were seen as safest.

These grouped insights supported what the plots hinted at: car type and brand matter in how risk is perceived.

## Key Findings
#### 1. Symboling and Normalized Losses Are Aligned
- There’s a strong positive correlation between symboling and normalized losses.
- Cars rated as riskier by manufacturers (higher symboling) tend to incur higher insurance losses.
- Convertibles (2.83) and hardtops (1.88) carry the highest average symboling scores, suggesting higher risk.
- Brands like Porsche (2.60), Saab (2.50), and Alfa-Romeo (2.33) rank highest in symboling, while Volvo (-1.27) ranks the lowest.

#### 2. Performance and Price Drive Insurance Losses
- Normalized losses have strong positive correlations with Horsepower & Car Price
- Weak positive correlation with engine size.
- These features suggest that high-performance and luxury vehicles tend to result in higher insurance payouts.

#### 3. Fewer Doors = Higher Risk
- There is a strong negative correlation between symboling and the number of doors.
- Cars with fewer doors (especially 2-door convertibles) are rated as riskier.
- Convertibles and hardtops have both fewer doors and higher symboling, reinforcing this pattern.

#### 4. Fuel Efficiency Shows Slight Risk Reduction
- Highway MPG has a weak negative correlation with normalized losses.
- Cars that are more fuel-efficient tend to have slightly lower insurance losses.

## Key Insights
- Manufacturer-assigned symboling is a reliable predictor of real insurance risk. Insurers should factor this into premium calculation and risk assessment models.
- Premiums should be adjusted upward for high-powered, expensive vehicles. These cars are more costly to repair or replace and more likely to be involved in accidents.
- Fewer-door vehicles, especially sporty body styles, should be considered higher risk when setting insurance rates.
- While not a major factor, fuel efficiency can be used as a minor risk-reducing variable in pricing strategies.
