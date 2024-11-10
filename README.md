# Project Summary

This project measures the credit risk model for LendingClub, a leading peer-to-peer lending company in the U.S., following major regulatory standards like Basel III, IFRS 9, and CEBS guidelines. The goal is to create a daily-use credit scoring tool that calculates the risk of borrower defaults and assesses potential financial losses for LendingClub. This model aims to enhance decision-making and ensure compliance with credit risk management regulations.

**To make the project accessible to all, let’s define the key concepts:**

* Probability of Default (PD): PD estimates the likelihood that a borrower will be unable to repay their loan. This probability is calculated using historical data and helps predict how likely it is that a loan will go unpaid.
* Exposure at Default (EAD): EAD represents the total value that a lender stands to lose if a borrower defaults on a loan. It calculates the amount of money at risk at the time of default.
* Loss Given Default (LGD): LGD estimates the portion of a loan that cannot be recovered if the borrower defaults. It’s often expressed as a percentage, representing the share of the total exposure that would be lost.
* Expected Loss (EL): EL combines PD, EAD, and LGD to calculate the total expected credit loss. This metric gives a comprehensive view of potential financial risk for the lender.
* The project’s design focuses on making each of these components interpretable and easy to apply for daily risk assessments. Here's a step-by-step look at the project:
* Data Preparation: Key loan data features are organized and transformed into categorical variables to maximize predictive accuracy and support interpretability.
* Building the PD Model: Using logistic regression, the Probability of Default model is developed to estimate the likelihood of loan defaults.
* Daily Scorecard: The PD model’s output is used to create a scorecard (in CSV format) that LendingClub can use for daily risk assessments, providing a straightforward way to interpret credit risk.
* Building the LGD Model: A beta regression model is created to predict the portion of exposure that might be lost in case of a default.
* Building the EAD Model: Linear regression is used to estimate the exposure amount in the event of default.
* Calculating Expected Loss (EL): After obtaining PD, LGD, and EAD, the Expected Loss is calculated as the product of these three components, giving a reliable estimate of potential losses.

## Key Features & Deliverables

* Interpretability: The model is designed to be transparent, allowing clear insights into how different variables influence credit risk—meaning it isn’t a “black box” that’s difficult to understand.

•	Regulatory Compliance: The project is built to align with Basel III, IFRS 9, and CEBS standards, all of which set guidelines for credit risk measurement.

•	Direct Default Probability Output: The PD model directly provides default probabilities, enhancing the accuracy of predictions.

•	High Accuracy and Stability: Designed for reliable predictions, the model's performance is periodically reviewed with updated data.

•	Scalability: The model can handle large volumes of data, making it suitable for real-time predictions.
Project Deliverables

•	Scorecard: An easily interpretable scoring tool in CSV format to assist in daily risk assessments.

•	Borrower Screening Tool: A system to assess the effect of various cut-off scores on borrower acceptance rates.

•	PD, LGD, and EAD Models: Integrated models covering the three critical metrics for credit risk.

•	Population Stability Index (PSI): A system to track model performance on new data to ensure ongoing accuracy.

**Dataset**

The project uses a dataset of over 800,000 LendingClub loans (sourced from Kaggle) issued between 2007 and 2015. The data is split into training (2007–2014) and validation (2015) sets to ensure that the model performs well on recent data, confirming that predictions remain accurate as market dynamics evolve.
Dataset - https://www.kaggle.com/datasets/premkumarrrs1411/credit-risk-modelling-loan-data/data
                                                                                                
1 Preprocessing - Data Preparation and Transformation

The preprocessing stage of this project involves transforming the raw dataset into a clean, structured format suitable for building a predictive model. This process includes handling categorical variables, dealing with missing data, and performing necessary transformations for feature engineering, particularly for credit risk modeling. Below are the key steps followed in this stage.

1.1 Importing Data

The dataset is loaded from its source (e.g., CSV or database) and made ready for exploration and analysis.

1.2 Exploring Data

A thorough examination of the dataset is performed to understand its structure, variables, and basic statistics. This step helps identify any data quality issues such as missing values, duplicates, or inconsistencies.

1.3 Creating Dummy Variables for Discrete Variables

Discrete variables are categorical in nature and need to be converted into numerical format for modeling purposes. This is done by creating dummy variables for all discrete variables in the dataset. The variables that are processed include:
•	grade: Assigned loan grade.
•	sub_grade: Loan subgrade assigned by LendingClub.
•	home_ownership: Borrower's homeownership status (values: RENT, OWN, MORTGAGE, OTHER).
•	loan_status: The loan's current status (values: Charged Off, Current, Default, Fully Paid, etc.).
•	addr_state: Borrower's state of residence.
•	verification_status: Indicates whether borrower’s income was verified.
•	purpose: Purpose of the loan as specified by the borrower.
•	initial_list_status: The initial listing status of the loan (values: W, F).
Dummy variables are created for each of these categorical variables to allow the model to process them efficiently.

1.4 Concatenating Dummy Variables

The newly created dummy variables are concatenated with the original dataset, ensuring that the dataset now contains both the original and the transformed features for further analysis and modeling.

1.5 Converting Date Formats

For variables that contain date information, the dates are converted into meaningful numerical features:
•	earliest_cr_line: This represents the date the borrower's earliest reported credit line was opened. The column is transformed into mths_since_earliest_cr_line to represent the number of months since this credit line was opened, using December 2017 as a reference point. Any future dates are adjusted to the maximum valid value within the dataset, and negative values are treated as data inconsistencies and adjusted to maintain data integrity.
•	emp_length: Employment length in years, transformed into an integer column emp_length_int. Values range from 0 to 10, where 0 represents less than one year of employment and 10 represents 10 years or more.
•	term: The term of the loan in months, transformed into term_int.
•	issue_d: The loan issue date, transformed into mths_since_issue_d, which calculates the months since the loan was issued relative to December 2017.

1.6 Handling Missing Values

Any missing or null values in the dataset are carefully handled. This may include:
•	Imputing missing values with appropriate techniques (mean, median, or mode imputation).
•	Dropping rows or columns with excessive missing data.
•	Ensuring that the dataset is complete for model training.

1.7 Setting the Target Variable

The loan_status variable is set as the dependent (target) variable, indicating whether a loan was paid off or defaulted. This variable is crucial for credit risk prediction and will serve as the model’s output.

1.8 Splitting Data into Training and Testing Sets

The dataset is split into training and testing subsets to ensure that the model is trained on one set of data and validated on another. This helps to assess the generalizability of the model and avoid overfitting.

1.9 Weight of Evidence (WoE) and Information Value (IV) Calculation

To improve model performance and interpretability, Weight of Evidence (WoE) and Information Value (IV) are calculated for both discrete and continuous variables.

•	WoE Calculation: Measures the strength of a variable in predicting the target by comparing the distribution of "Goods" (non-events) to "Bads" (events). It is calculated for each bin of a variable.
Formula for WoE:

WoE= ln {{Distribution of Goods}/{{Distribution of Bads}}

•	IV Calculation: Measures the predictive power of an independent variable, helping identify which features are most important for the target variable. The IV is computed for each variable by summing the contribution of each bin based on WoE values.

Formula for IV:
IV = ∑ (% of non-events - % of events) * WOE


 IV Categories:

 IV < 0.02: Not useful for prediction.

 0.02 ≤ IV < 0.1: Weak predictive power.

 0.1 ≤ IV < 0.3: Medium predictive power.

 0.3 ≤ IV < 0.5: Strong predictive power.

 IV > 0.5: Suspiciously high predictive power, suggesting potential overfitting.

These steps ensure that features with high predictive power are retained, while reducing noise from less relevant features.

1.10 Interpreting WoE Plot: The WoE plot provides a visual representation of the predictive strength for each bin of a variable. Positive WoE values indicate that a bin is more likely associated with “Goods” (non-default), whereas negative WoE values suggest a stronger likelihood of being associated with “Bads” (default). Consistent patterns in WoE values across bins signal a strong predictor, whereas erratic WoE patterns may indicate noise or non-informative features.

Fine and Coarse Classing

To enhance the predictive strength of continuous variables, Fine Classing and Coarse Classing are applied based on the insights we got from calculating and plotting the WoE.

Fine Classing: Creates 10 to 20 bins/groups for a continuous variable, allowing for a detailed calculation of WoE and IV. Each bin represents a small range of the continuous variable, capturing subtle changes in predictive power.

Coarse Classing: Groups adjacent bins with similar WoE scores, reducing the number of bins. This technique provides a simplified and aggregated view of the variable, reducing noise and making the model more interpretable.

10.11 Exporting Preprocessed Data
     





