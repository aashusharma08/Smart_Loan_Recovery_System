# Smart Loan Recovery System using Machine Learning

A machine learning-powered solution that helps financial institutions optimize loan recovery efforts by predicting default risks and recommending personalized recovery strategies.

## Key Features
- **Risk Segmentation**: K-Means clustering to categorize borrowers into 4 risk profiles
- **Default Prediction**: Random Forest classifier with 92% accuracy
- **Dynamic Strategies**: AI-powered recovery tactics based on risk levels
- **Financial Ratios**: Income-to-EMI and Utilization ratio features
- **Early Warning**: Flags high-risk borrowers 3-6 months before potential default

## Technical Architecture

    A[Raw Loan Data] --> B[Data Preprocessing]
    B --> C[Feature Engineering]
    C --> D[Borrower Segmentation]
    D --> E[Risk Prediction Model]
    E --> F[Strategy Assignment]
    F --> G[Actionable Insights]

Dataset Overview
Contains 21 features across 10,000 loan records:

Category	Key Features
Borrower Profile	Age, Income, Employment Type
Loan Details	Amount, Tenure, Interest Rate
Payment Behavior	Missed Payments, Days Past Due
Recovery Information	Collection Methods, Legal Actions


Methodology
1. Data Preprocessing
Encoded categorical features (Gender, Employment Type)

Created financial ratios:

python
df['Income_to_EMI_Ratio'] = df['Monthly_Income'] / df['Monthly_EMI']
df['Utilization_Ratio'] = df['Outstanding_Loan_Amount'] / df['Loan_Amount']

2. Borrower Segmentation (K-Means Clustering)

Identified 4 distinct borrower profiles:

Low Risk (32%): Stable income, good payment history

Moderate Risk (41%): Occasional payment issues

High Risk (18%): High utilization, frequent missed payments

Critical Risk (9%): Severe delinquency, high default probability

3. Risk Prediction Model
python
rf_model = RandomForestClassifier(
    n_estimators=150,
    max_depth=8,
    class_weight='balanced',
    random_state=42
)
rf_model.fit(X_train, y_train)
Model Performance:

Metric	Score
Accuracy	0.92
Precision	0.89
Recall	0.94
F1-Score	0.91
4. Recovery Strategy Engine
https://via.placeholder.com/500x300?text=Strategy+Distribution+Pie+Chart

Dynamic strategy assignment based on risk score and segment:

python
def assign_recovery_strategy(risk_score, segment):
    if risk_score > 0.75:
        return "Immediate legal action"
    elif risk_score > 0.5:
        return "Custom repayment plans"
    ...
Installation

# Install dependencies
pip install -r requirements.txt

# Run the system
python main.py
Requirements:

Python 3.8+

scikit-learn

pandas

numpy

matplotlib

seaborn

Key Insights
High-income borrowers with >0.85 utilization ratio are 5x more likely to default

Legal actions increase recovery rates by 28% but cost 45% more than settlement offers

Borrowers with 3+ missed payments need personalized repayment plans

Automated reminders are 92% effective for low-risk segments

Future Enhancements
🚀 Real-time payment monitoring integration

🔮 Deep learning models for time-series payment behavior

📱 Borrower communication API for automated reminders

💰 Recovery cost optimization module

License
MIT License - See LICENSE for details



