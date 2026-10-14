# Credit Card Fraud Detection with Machine Learning

*[Clique aqui para a versão em português](README.md)*

This project was developed as the **Capstone Project** for the **Data Science Course** at **EBAC (British School of Creative Arts and Technology)**.

During development — especially during the fine-tuning stages and resolving computer performance bottlenecks (such as the freezing of the SVM artificial intelligence algorithm) —, I utilized AI tools to find faster solutions and implement programming best practices.

---

### The Problem This Project Solves

The goal is to build an intelligent system capable of **identifying fraudulent credit card transactions in real time**, allowing banks to block suspicious purchases before financial damage occurs.

All of this is done while maintaining a delicate balance: **blocking fraud without disrupting the customer's daily life** (avoiding the frustration of having a legitimate purchase mistakenly declined).

---

### How the Project Was Built (Step by Step)

To solve this problem, the project followed four main steps:

* **Data Organization:** The data was split evenly into "train" (for the system to learn) and "test" (to prove it works in practice), ensuring that the real-world proportion of fraud was maintained.
* **Standardization:** Information like transaction *Time* and *Amount* underwent a mathematical adjustment so that extremely high or unusual numbers wouldn't confuse the system.
* **Imbalance Correction:** Since the vast majority of daily transactions are legitimate and fraud is rare, the system used a special technique (called SMOTE) to generate controlled "example frauds." This helped the algorithim better recognize scams without bloating the database size.
* **Fine-Tuning (Optimization):** The system automatically tested hundreds of combinations of mathematical settings to find the fastest and most accurate configuration.

---

### Tested Models and the Winner

The models were put to the test by simulating a real-world scenario (using imbalanced data):

* **XGBoost (The Grand Winner):** This model delivered the best overall balance. It achieved **83% accuracy when flagging fraud** (Precision) and successfully **caught 87% of all actual frauds** (Recall).
* **Logistic Regression:** It managed to catch most frauds (89% Recall) but triggered too many false alarms — blocking the cards of many innocent customers (only 20% precision).
* **Linear SVM:** Performance was hindered because the processing became too heavy and had to be stopped before completing all tests.

#### Final Security Adjustment
To further protect the customer, **XGBoost** went through a "sensitivity filter": the threshold required for the system to flag fraud was increased. As a result, precision jumped to **90%**, ensuring very few innocent customers had their cards blocked by mistake, while maintaining a strong fraud detection rate of **84%**.


* * *

### Files Generated for Production

Upon completion of the script, and to simulate a real-world production deployment scenario, I generated three files for loading:

*   `modelo_xgb.pkl`: the fitted model;
*   `robust_scaler.pkl`: the normalization file;
*   `threshold_calibrado.pkl`: the defined optimal cutoff point.

* * *

### Featured Visualizations

![Precision-Recall Curve](images_fraud/curva_pr.png)

![Transaction Amount Distributions by Class](images_fraud/boxplot_amount_class.png)

![Feature Importance](images_fraud/importancia_variaveis.png)

*Note: This project was developed for academic and professional portfolio purposes.*
