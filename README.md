# AI Profit Forecasting Tool for Digital Marketing Proposals

## 1. Project Summary
The **AI Profit Forecasting Tool** is a machine learning–powered web application that predicts the potential **quarterly profit** for our company after submitting a proposal to a prospective client. By analysing past proposals, historical revenue, delivery costs, and client characteristics, the system helps the sales and management teams prioritise high-profit opportunities, set smarter pricing, and allocate resources efficiently.

---

## 2. Problem Statement
Currently, our sales team sends digital marketing proposals without an accurate, data-driven forecast of profitability. This can lead to:
- Overcommitting resources to low-margin clients
- Missing opportunities with high-profit potential
- Inaccurate financial planning for upcoming quarters

Without a profit forecast model, our team relies heavily on intuition, which can be biased and inconsistent.

---

## 2.5 Use Case & Workflow
**Primary User:** Sales team members and management within our digital marketing agency.

**Workflow:**
1. A sales rep drafts a proposal for a potential client in the proposal platform.
2. The proposal details are submitted to the AI Profit Forecasting Tool.
3. The AI model analyses the data and predicts profit for each of the next 4 quarters.
4. The dashboard displays:
   - Forecasted profit values
   - Confidence scores
   - Key factors influencing the prediction
5. The sales team uses these insights to:
   - Decide whether to pursue or adjust the proposal
   - Set more competitive and profitable pricing
   - Plan resource allocation for service delivery

---

## 3. AI-Powered Solution
We propose developing an AI-driven prediction model that:
- **Inputs:** Proposal details, client profile, industry, proposed services, estimated delivery costs, and historical deal outcomes
- **Outputs:** Predicted profit for each of the next 4 quarters (if the deal is won), along with a confidence score and the top factors influencing the prediction

**Example Workflow:**
1. Sales rep drafts a proposal and enters details into the system.
2. The model analyses the data against historical patterns.
3. The tool displays predicted quarterly profit, confidence level, and reasons for the prediction.

---

## 4. Technical Architecture

**Data Sources:**
- Historical proposals (value, services offered, pricing structure, discounts)
- Client information (industry, size, location)
- Historical revenue and cost breakdowns
- Win/loss status and deal timelines

**Machine Learning Pipeline:**
1. **Data Preprocessing:** Clean, normalise, and anonymise client data
2. **Feature Engineering:** Extract predictive features (proposal size, industry sector, cost ratio, services mix)
3. **Model Selection:** Gradient Boosting (XGBoost/LightGBM) or Random Forest Regression
4. **Evaluation Metrics:** Mean Absolute Error (MAE) and R² score
5. **Explainability Layer:** SHAP values to identify key factors driving predictions

**System Components:**
- **Backend API:** Python (FastAPI) serving the trained ML model
- **Frontend Dashboard:** React or similar for user input & displaying results
- **Database:** PostgreSQL/MySQL for storing proposals & predictions
- **Hosting:** AWS, GCP, or Azure

**Architecture Flow:**
```
[Proposal Submission] → [API Receives Data] → [ML Model Predicts Profit]
→ [Confidence Score + Key Drivers] → [Dashboard Displays Results]
```

---

## 4.5 AI Features to Be Implemented
- **Prompt Engineering:** If an LLM is used to generate human-readable explanations of predictions, prompts will be structured to request concise, business-focused insights. *Relevance: Sales teams need clear, actionable explanations to understand why a proposal is predicted to be profitable, helping them adjust strategies accordingly.*

- **Structured Outputs:** Predictions and explanations will be returned in JSON format, containing `profit_forecast`, `confidence_score`, and `key_factors`. *Relevance: Structured data enables easy integration with existing CRM systems and allows for automated decision-making workflows.*

- **Retrieval-Augmented Generation (RAG):** Historical proposal data can be stored in a vector database (e.g., Pinecone, Weaviate) for retrieving similar past deals to provide context alongside predictions. *Relevance: By finding similar historical proposals, the system can provide more accurate predictions and explain patterns based on actual past outcomes.*

- **Evaluation Frameworks:** Model accuracy will be measured using MAE and R²; predictions will be compared against actual profits. *Relevance: Continuous evaluation ensures the model remains accurate as market conditions change and new data becomes available.*

- **Observability Tools:** MLflow for model performance tracking, and API monitoring for response time and error rates. *Relevance: Monitoring helps identify when the model needs retraining and ensures reliable service for sales teams making time-sensitive decisions.*

---

## 4.6 Example Prompts & Expected Outputs

**Prompt 1 - Profit Prediction:**
```
Analyze the following proposal for a digital marketing client:
- Client Industry: E-commerce
- Proposal Value: €50,000
- Services: SEO (40%), PPC (35%), Content Marketing (25%)
- Client Size: Mid-market (100-500 employees)
- Historical Win Rate in Industry: 75%

Predict quarterly profit for the next 4 quarters and provide confidence score.
```

**Expected Output 1 (JSON Structured):**
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
```

**Prompt 2 - Explanation Generation:**
```
Given the following proposal data and profit prediction, explain the top three reasons why the predicted profit is €15,000 for Q1:
{proposal_data}
{prediction_data}

Focus on business insights that would help the sales team understand the prediction.
```

**Expected Output 2 (Structured Explanation):**
```json
{
  "explanation": {
    "primary_reason": "Strong historical performance in e-commerce sector with 75% win rate",
    "secondary_reason": "Optimal service mix with 75% allocated to high-margin services (SEO + PPC)",
    "tertiary_reason": "Proposal value aligns with profitable deal size range (€40k-€60k)",
    "recommendation": "Consider slight price increase as confidence score indicates room for margin improvement"
  }
}
```

---

## 4.7 Evaluation Strategy
**Technical Metrics:**
- Mean Absolute Error (MAE) to measure average prediction error
- R² score to measure how well predictions explain variance in actual profit

**Business Metrics:**
- Percentage of correctly identified high-profit deals
- Increase in average profit per signed deal after using the tool

---

## 4.8 Observability Plan
- **Model Monitoring:** Track prediction accuracy over time and retrain quarterly
- **Error Tracking:** Log all failed predictions or anomalies in inputs
- **Usage Analytics:** Monitor how often sales reps consult the prediction before closing deals
- **Tooling:** MLflow for experiment tracking, Prometheus or similar for API metrics, and custom logging for dashboard usage

---

## 5. Implementation Plan

### Phase 1 – Data Preparation
- Collect historical proposal, revenue, and cost data
- Clean and standardise datasets
- Ensure GDPR compliance through anonymisation

### Phase 2 – Model Development
- Feature engineering & selection
- Train initial regression model
- Validate with hold-out test set

### Phase 3 – Application Build
- Develop backend API to serve predictions
- Build a simple web dashboard for internal use

### Phase 4 – Deployment
- Deploy model and API to cloud environment
- Integrate dashboard for sales team access

### Phase 5 – Monitoring & Iteration
- Monitor model accuracy
- Retrain quarterly with new data

---

## 6. Potential Challenges & Mitigations
- **Small Dataset:** Augment with industry benchmarks and synthetic data generation
- **Changing Market Conditions:** Retrain model regularly to adapt to shifts in marketing ROI
- **Data Privacy:** Fully anonymise client identifiers before processing

---

## 7. Expected Benefits & Impact
- **Higher Profit Margins:** Focus on high-profit deals
- **Smarter Resource Allocation:** Avoid overspending on low-margin clients
- **Data-Driven Pricing:** Adjust proposals for optimal profitability
- **Improved Forecast Accuracy:** Better quarterly financial planning

---

## 8. Future Enhancements
- Integrate real-time ad performance data post-deal to refine predictions
- Add "what-if" scenario testing for different proposal configurations
- Incorporate macroeconomic indicators to improve forecast precision

---

**Author:** Liam Gosnell
**Date:** 12 August 2025


