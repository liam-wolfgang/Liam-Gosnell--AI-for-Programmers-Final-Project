```markdown
# AI Profit Forecasting Tool for Digital Marketing Proposals

## 1. Project Summary
The **AI Profit Forecasting Tool** is a machine learning–powered web application that predicts the potential **quarterly profit** for our company after submitting a proposal to a prospective client. By analysing past proposals, historical revenue, delivery costs, and client characteristics, the system helps the sales and management teams to prioritise high-profit opportunities, set smarter pricing, and allocate resources efficiently.

---

## 2. Problem Statement
Currently, our sales team sends digital marketing proposals without an accurate, data-driven forecast of profitability. This can lead to:
- Overcommitting resources to low-margin clients
- Missing opportunities with high-profit potential
- Inaccurate financial planning for upcoming quarters

Without a profit forecast model, our team relies heavily on intuition — often biased and inconsistent.

---

## 3. Use Case & Workflow
**Primary User:** Sales team members and management within our digital marketing agency.

**Workflow:**
1. A sales representative drafts a proposal for a potential client in the proposal platform.
2. The proposal details are submitted to the AI Profit Forecasting Tool.
3. The AI model analyses the data and predicts profit for each of the next four quarters.
4. The dashboard displays:
   - Forecasted profit values
   - Confidence scores
   - Key factors influencing the prediction
5. The sales team uses these insights to:
   - Decide whether to pursue or adjust the proposal
   - Set more competitive and profitable pricing
   - Plan resource allocation for service delivery

---

## 4. AI-Powered Solution
We propose developing an AI-driven prediction model that:
- **Inputs:** Proposal details, client profile, industry, proposed services, estimated delivery costs, and historical deal outcomes
- **Outputs:** Predicted profit for each of the next four quarters (if the deal is won), along with a confidence score and the top factors influencing the prediction

**Example Workflow:**
1. Sales representative drafts a proposal and enters details into the system.
2. The model analyses the data against historical patterns.
3. The tool displays predicted quarterly profit, confidence level, and reasons for the prediction.

---

## 5. Technical Architecture
**Data Sources:**
- Historical proposals (value, services offered, pricing structure, discounts)
- Client information (industry, size, location)
- Historical revenue and cost breakdowns
- Win/loss status and deal timelines

**Machine Learning Pipeline:**
1. **Data Pre-processing:** Clean, normalise, and anonymise client data
2. **Feature Engineering:** Extract predictive features (proposal size, industry sector, cost ratio, services mix)
3. **Model Selection:** Gradient Boosting (XGBoost/LightGBM) or Random Forest Regression
4. **Evaluation Metrics:** Mean Absolute Error (MAE) and R² score
5. **Explainability Layer:** SHAP values to identify key factors driving predictions

**System Components:**
- **Backend API:** Python (FastAPI) serving the trained ML model
- **Frontend Dashboard:** React or similar for user input and displaying results
- **Database:** PostgreSQL/MySQL for storing proposals and predictions
- **Hosting:** AWS, GCP, or Azure

**Architecture Flow:**
```

\[Proposal Submission] → \[API Receives Data] → \[ML Model Predicts Profit]
→ \[Confidence Score + Key Drivers] → \[Dashboard Displays Results]

```

---

## 6. AI Features to Be Implemented
- **Prompt Engineering:** If an LLM is used to generate human-readable explanations of predictions, prompts will be structured to produce concise, business-focused insights.
- **Structured Outputs:** Predictions and explanations will be returned in JSON format, containing `profit_forecast`, `confidence_score`, and `key_factors`.
- **Retrieval-Augmented Generation (RAG):** Historical proposal data stored in a vector database to retrieve similar past deals for context.
- **Evaluation Frameworks:** Model accuracy measured using MAE and R², compared against actual profits.
- **Observability Tools:** MLflow for performance tracking, API monitoring for response times and errors.

---

## 7. Example Prompts & Expected Outputs
**Prompt 1 – Profit Prediction:**
```

Analyse the following proposal for a digital marketing client:

* Client Industry: E-commerce
* Proposal Value: €50,000
* Services: SEO (40%), PPC (35%), Content Marketing (25%)
* Client Size: Mid-market (100–500 employees)
* Historical Win Rate in Industry: 75%

Predict quarterly profit for the next four quarters and provide a confidence score.

````
**Expected Output 1:**
```json
{
  "predicted_profit": {
    "Q1": 15000,
    "Q2": 17500,
    "Q3": 18000,
    "Q4": 16000
  },
  "confidence_score": 0.87,
  "key_factors": [
    "High historical win rate in client's industry",
    "Service mix includes high-margin SEO and PPC",
    "Discount offered is within optimal profitability range"
  ]
}
````

**Prompt 2 – Explanation Generation:**

```
Given the following proposal data and profit prediction, explain the top three reasons why the predicted profit is €15,000 for Q1:
{proposal_data}
{prediction_data}

Focus on business insights that would help the sales team understand the prediction.
```

**Expected Output 2:**

```json
{
  "explanation": {
    "primary_reason": "Strong historical performance in the e-commerce sector with a 75% win rate",
    "secondary_reason": "Optimal service mix with 75% allocated to high-margin services (SEO + PPC)",
    "tertiary_reason": "Proposal value aligns with the profitable deal size range (€40k–€60k)",
    "recommendation": "Consider a slight price increase as the confidence score indicates room for margin improvement"
  }
}
```

---

## 8. Evaluation Strategy

**Technical Metrics:**

* Mean Absolute Error (MAE)
* R² score
  **Business Metrics:**
* % of correctly identified high-profit deals
* Increase in average profit per signed deal

---

## 9. Observability Plan

* Model accuracy tracking and quarterly retraining
* Error logging for failed predictions or anomalies
* Usage analytics for sales team interactions
* MLflow, Prometheus, and custom logging tools

---

## 10. Implementation Plan

**Phase 1:** Data preparation and GDPR compliance
**Phase 2:** Model development and validation
**Phase 3:** Application build (backend + dashboard)
**Phase 4:** Deployment to cloud
**Phase 5:** Monitoring and quarterly updates

---

## 11. Potential Challenges & Mitigations

* Small datasets → Use benchmarks and synthetic data
* Market changes → Regular retraining
* Data privacy → Full anonymisation

---

## 12. Expected Benefits & Impact

* Higher profit margins
* Smarter resource allocation
* Data-driven pricing
* Improved forecast accuracy

---

## 13. Future Enhancements

* Integrate post-deal ad performance data
* Add “what-if” scenario testing
* Incorporate macroeconomic indicators

---

**Author:** Liam Gosnell
**Date:** 12 August 2025

```
```
