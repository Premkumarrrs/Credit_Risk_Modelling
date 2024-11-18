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

*	Regulatory Compliance: The project is built to align with Basel III, IFRS 9, and CEBS standards, all of which set guidelines for credit risk measurement.

*	Direct Default Probability Output: The PD model directly provides default probabilities, enhancing the accuracy of predictions.

*	High Accuracy and Stability: Designed for reliable predictions, the model's performance is periodically reviewed with updated data.

*	Scalability: The model can handle large volumes of data, making it suitable for real-time predictions.
Project Deliverables

*	Scorecard: An easily interpretable scoring tool in CSV format to assist in daily risk assessments.

*	Borrower Screening Tool: A system to assess the effect of various cut-off scores on borrower acceptance rates.

*	PD, LGD, and EAD Models: Integrated models covering the three critical metrics for credit risk.

*	Population Stability Index (PSI): A system to track model performance on new data to ensure ongoing accuracy.

## Dataset

The project uses a dataset of over 800,000 LendingClub loans (sourced from Kaggle) issued between 2007 and 2015. The data is split into training (2007–2014) and validation (2015) sets to ensure that the model performs well on recent data, confirming that predictions remain accurate as market dynamics evolve.
Dataset - https://www.kaggle.com/datasets/premkumarrrs1411/credit-risk-modelling-loan-data/data


## Pipeline - 
* Preprocessing:
Creation of dummy variables.
Calculation of Weight of Evidence (WoE) and Information Value (IV).
Fine and coarse classing of variables.

* Probability of Default (PD), Scorecard, and Credit Score Cutoffs:
Development of the PD model using logistic regression.
Conducting statistical validation tests.
Building the scorecard.
Determining the cutoff rate for accepting credit demand.

* Loss Given Default (LGD), Exposure at Default (EAD), and Expected Loss (EL) Calculation:
LGD modeling with beta regression.
EAD modeling with linear regression.
Calculation of expected loss.
Evaluation of model performance.

* Monitoring - Population Stability Index (PSI):
Assessing whether the model performs well with new data over time.
                                                                                               

     





