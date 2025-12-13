🛍️ Retail Transaction Analysis & Membership Targeting
Regression & Classification Project

This project analyzes a retail transaction dataset to understand transaction value drivers and to identify non-member customers (Negative class) for targeted promotional strategies.

The analysis strictly uses only the available dataset features (no fabricated or synthetic data) and applies both Regression and Classification techniques to extract business-relevant insights.

📌 1. Project Overview

This project consists of two main analytical components:

1️⃣ Regression Analysis

Predicts transaction price (purchase amount)

Identifies factors that increase or decrease spending per transaction

2️⃣ Classification Analysis

Predicts membership status

Focuses on Not Member (Negative class) identification

Supports promotional targeting for customer acquisition campaigns

The project emphasizes interpretability and business usability over model complexity.

📌 2. Dataset Description

The dataset contains transaction-level retail data with the following columns:

✅ Available Features

Category – Product category (Clothing, Footwear, Accessories, Outerwear)

Price – Total transaction amount (used as regression target)

Quantity – Number of items purchased

Discount Flag – Whether a discount was used (Yes / No)

Payment Method – Cash, Credit Card, Wallet

Membership Status – Member (1) / Not Member (0)

❌ Dataset Limitations

No customer ID

No timestamps or purchase dates

No discount percentage

No repeat-customer tracking

All modeling decisions respect these constraints.

📌 3. Business Objective
🎯 Primary Business Question

How can we identify non-member customers and design promotions to convert them into members?

Supporting Questions

Which transactions are most likely from non-members?

Do non-members behave differently in terms of price, quantity, or discount usage?

Can we reliably detect non-members to target promotions efficiently?

📌 Key Design Choice:
This project intentionally focuses on the Negative class (Not Member = 0) because:

Promotions are typically sent to non-members, not existing members

Misclassifying a member as non-member is less costly than missing a true non-member

📌 4. Features & Targets
🎯 Regression Target

Price (continuous numeric value)

🎯 Classification Target

Membership Status

0 = Not Member (Negative class of interest)

1 = Member

🧱 Features Used
Feature	Type	Rationale
Category	Categorical (One-hot)	Strong determinant of spending
Quantity	Numeric	Direct impact on price
Discount Flag	Binary (0/1)	Promotional behavior indicator
Payment Method	Categorical (One-hot)	Possible spending pattern differences

No engineered or synthetic features were added.

📌 5. Methodology
🔹 Step 1: Data Cleaning

Handled missing values

Encoded categorical variables

Converted Discount Flag to binary

🔹 Step 2: Exploratory Data Analysis (EDA)

Price distribution analysis

Category vs transaction value

Discount vs non-discount spending comparison

Payment method spending patterns

🔹 Step 3: Regression Modeling

Linear Regression

Train/Test split

Evaluation metrics:

MAE

RMSE

R² Score

Residual diagnostics

🔹 Step 4: Classification Modeling

Logistic Regression

Focus on interpretability and probability-based outputs

Confusion Matrix & Classification Report analysis

📌 6. Key Insights from EDA

Clothing generates the highest transaction volume.

Accessories show higher average transaction values.

Non-discount transactions tend to have higher prices than discounted ones.

Payment methods show minimal spending differences, indicating channel neutrality.

Lack of timestamp data prevents seasonality analysis.

📊 7. Classification Model Results
Logistic Regression (Membership Prediction)
✔ Overall Accuracy

Accuracy: 83%

The model correctly classifies membership status for 83% of transactions.

📌 Classification Report
Class	Precision	Recall	F1-score	Support
0 – Not Member	1.00	0.76	0.86	558
1 – Member	0.62	0.99	0.76	222

Macro Avg F1-score: 0.81

Weighted Avg F1-score: 0.83

🔍 Interpretation (Negative Class Focus)
🟥 Not Member (Class 0 — Business Priority)

Precision = 1.00
→ Every transaction predicted as Not Member is truly a non-member

Recall = 0.76
→ The model successfully identifies 76% of all non-members

📌 Business Value:
This makes the model highly reliable for promotion targeting, as marketing resources are not wasted on actual members.

📌 Confusion Matrix Summary
Actual ↓ / Predicted →	Not Member (0)	Member (1)
Not Member (0)	424	134
Member (1)	2	220
Key Observations

424 non-members correctly identified

134 non-members misclassified as members

Only 2 members incorrectly targeted as non-members

📌 The model strongly minimizes false targeting of members, which aligns well with promotional use cases.

⭐ Final Business Conclusion

Logistic Regression provides interpretable and reliable results

The model is well-suited for identifying non-members, the key target group for promotions

High precision on the negative class ensures efficient marketing spend

Regression insights complement classification by explaining spending behavior
