# KAIM_WEEK3 - AlphaCare Insurance Solutions: Car Insurance Risk & Predictive Analytics

## Project Overview

This project focuses on leveraging historical car insurance claim data from **AlphaCare Insurance Solutions (ACIS)** in South Africa to develop cutting-edge risk and predictive analytics. As a marketing analytics engineer, the primary objective is to **optimize marketing strategies** and **identify "low-risk" client segments** for whom premium reductions could be offered, thereby attracting new clients.

## Motivation

This challenge is designed to significantly enhance skills in **Data Engineering (DE)**, **Predictive Analytics (PA)**, and **Machine Learning Engineering (MLE)**. It provides a realistic simulation of the pressures and deadlines common in financial analytics, demanding the ability to manage complex datasets, adapt to challenges, and think creatively. Through this analysis, you'll gain a deeper understanding of how hypothesis testing and predictive analytics are applied in the insurance sector.

## Key Tasks & Objectives

To achieve the business objectives, the project involves several key analytical areas:

### Insurance Terminologies

Familiarize yourself with fundamental insurance concepts and terms. Understanding how insurance operates is crucial for this project. At its core, insurance involves **premiums**, which are the regular payments made by the **policyholder** to maintain coverage. In return for these premiums, the insurer agrees to provide financial protection up to a defined **coverage limit** for covered losses, after the policyholder pays a **deductible**. The process of assessing this risk, considering factors like a client's profile and history, is known as **underwriting**. These foundational elements form the basis of all insurance transactions, ensuring both protection for the insured and sustainable operations for the insurer.

* **Resource:** [50 Common Insurance Terms and What They Mean — Cornerstone Insurance Brokers](https://www.cornerstone.co.za/blog/50-common-insurance-terms-and-what-they-mean/)

### A/B Hypothesis Testing

Understand the benefits of A/B hypothesis testing and rigorously test the following null hypotheses:

* **Null Hypothesis 1:** There are no risk differences across provinces.

* **Null Hypothesis 2:** There are no risk differences between zip codes.

* **Null Hypothesis 3:** There are no significant margin (profit) differences between zip codes.

* **Null Hypothesis 4:** There are no significant risk differences between women and men.

### Machine Learning & Statistical Modeling

* **Claims Prediction:** For each **zip code**, fit a **linear regression model** to predict the total claims.

* **Optimal Premium Prediction:** Develop a comprehensive **machine learning model** to predict optimal premium values, considering:

  * Car features (e.g., make, model, registration year, custom value estimate).

  * Owner features (e.g., marital status, gender, citizenship).

  * Location features (e.g., province, postal code, Cresta Zone).

  * Any other features found relevant during exploration.

* **Feature Importance:** Report on the explaining power of the most important features influencing your predictive model.

### Final Report

The culmination of this project is a detailed report that should:

* Detail the **methodologies used** for analysis and model development.

* Present the **findings** from all analyses, including A/B test results.

* Provide **recommendations** on plan features that could be modified or enhanced based on the test outcomes to tailor insurance products more effectively to consumer needs and preferences.

---

## Data

The historical insurance claim data covers the period from **February 2014 to August 2015**.

* **Data Source:** [Historical Insurance Claim Data](https://www.kaggle.com/datasets/prmohanty/car-insurance-claims-data) (Assuming this is the correct link based on the description's context)

The dataset includes columns categorized as follows:

* **Insurance Policy:** `UnderwrittenCoverID`, `PolicyID`, `TransactionDate`, `TransactionMonth`

* **Client Information:** `IsVATRegistered`, `Citizenship`, `LegalType`, `Title`, `Language`, `Bank`, `AccountType`, `MaritalStatus`, `Gender`

* **Client Location:** `Country`, `Province`, `PostalCode`, `MainCrestaZone`, `SubCrestaZone`

* **Car Insured:** `ItemType`, `Mmcode`, `VehicleType`, `RegistrationYear`, `Make`, `Model`, `Cylinders`, `Cubiccapacity`, `Kilowatts`, `Bodytype`, `NumberOfDoors`, `VehicleIntroDate`, `CustomValueEstimate`, `AlarmImmobiliser`, `TrackingDevice`, `CapitalOutstanding`, `NewVehicle`, `WrittenOff`, `Rebuilt`, `Converted`, `CrossBorder`, `NumberOfVehiclesInFleet`

* **Plan Details:** `SumInsured`, `TermFrequency`, `CalculatedPremiumPerTerm`, `ExcessSelected`, `CoverCategory`, `CoverType`, `CoverGroup`, `Section`, `Product`, `StatutoryClass`, `StatutoryRiskType`

* **Payment & Claim:** `TotalPremium`, `TotalClaims`

---

## Getting Started

To get a copy of the project up and running on your local machine, follow these simple steps.

### Prerequisites

Ensure you have the following installed on your system:

* **Python 3.8+**: This project is developed using Python.

* **pip**: Python's package installer, usually comes with Python.

* **git**: For cloning the repository from GitHub.

### Cloning the Repository

To get a local copy of the project, open your terminal or command prompt and run the following command:

```bash
git clone [https://github.com/your-username/alphacare-insurance-analytics.git](https://github.com/your-username/alphacare-insurance-analytics.git)
cd alphacare-insurance-analytics