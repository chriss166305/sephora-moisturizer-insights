# AI-Powered Sephora Customer Insights Automation

An AI-assisted customer-insights workflow that combines SQL analysis and Claude LLM classification to transform unstructured Sephora moisturizer reviews into actionable product and customer-experience recommendations.

## Business Problem

Customer reviews contain valuable feedback about product performance, but manually reading thousands of reviews is slow and inconsistent. This project explores how SQL and LLM automation can help companies identify customer pain points, satisfaction drivers, and product-improvement opportunities while retaining human oversight.

## Project Scope

* **Reviews analyzed with SQL:** 39,366
* **LLM classification sample:** 1,000 stratified reviews
* **Sample composition:** 600 negative, 200 mixed, and 200 positive reviews
* **Customer-experience taxonomy:** 13 categories
* **Analysis type:** Historical batch analysis

The stratified sample intentionally included more negative reviews to provide deeper coverage of customer pain points. Therefore, sample percentages should not be interpreted as population-wide prevalence estimates.

## Methodology

1. Audited and prepared the review dataset in Python.
2. Used SQL to identify satisfaction patterns across brands, products, price bands, skin types, and time.
3. Reviewed a 350-review discovery sample to develop a 13-category customer-experience taxonomy.
4. Tested and refined Claude prompts through one-review, 10-review, and 100-review evaluations.
5. Classified a stratified 1,000-review sample through the Claude Batch API.
6. Required standardized classifications supported by exact customer quotations.
7. Automatically accepted grounded classifications and routed uncertain cases for human review.
8. Aggregated the validated classifications into customer pain points, satisfaction drivers, and business recommendations.

## Automation and Validation Results

* **Reviews successfully processed:** 1,000
* **Processing errors:** 0
* **Validated aspect mentions:** 2,616
* **Aspect-level evidence grounding:** 98.16%
* **Automatically accepted reviews:** 876
* **Reviews routed for human review:** 124
* **Reduction in manual-review workload:** 87.6%
* **Actual Batch API cost:** $2.05

The 87.6% workload reduction represents the proportion of reviews that passed the automated validation rules and did not require individual manual review.

## Customer Insights

### Leading Customer Pain Points

* Skin reactions were the most frequently identified negative theme.
* Insufficient hydration was a major source of dissatisfaction.
* Texture and finish issues included stickiness, greasiness, and heaviness.
* Layering and absorption problems included pilling and poor makeup compatibility.
* Price concerns were often connected to whether product performance justified the cost.

### Leading Satisfaction Drivers

* Hydration was the strongest positive experience driver.
* Texture and finish strongly influenced favorable product experiences.
* Visible results included softness, smoothness, plumping, and improved skin appearance.
* Positive absorption and layering experiences supported product usability.

Because each review could contain multiple aspects, theme percentages are not mutually exclusive.

## Business Recommendations

1. Prioritize formula and product-compatibility reviews for products associated with skin reactions.
2. Protect hydration and texture performance during product reformulation.
3. Align product claims and positioning with customer-reported experiences.
4. Use skin-type feedback to improve product targeting and customer guidance.
5. Monitor recurring complaint themes and route unusual or high-risk feedback for human review.

## Human-in-the-Loop Design

The workflow does not treat every LLM classification as automatically correct. It uses:

* Standardized classification fields
* Exact-quote evidence validation
* Confidence thresholds
* Classification decision rules
* Automated intent corrections
* Human-review routing for ambiguous cases

This design allows the LLM to handle repetitive classification work while preserving human oversight for uncertain outputs.

## Repository Contents

| File                                      | Purpose                                                                  |
| ----------------------------------------- | ------------------------------------------------------------------------ |
| `01_data_audit_prep.ipynb`                | Data auditing, cleaning, filtering, and database preparation             |
| `02_sql_analysis.ipynb`                   | SQL-based customer satisfaction and segment analysis                     |
| `03_llm_classification.ipynb`             | Taxonomy development, prompt testing, API classification, and validation |
| `Outputs/llm_negative_theme_summary.csv`  | Aggregated negative customer themes                                      |
| `Outputs/llm_positive_driver_summary.csv` | Aggregated positive experience drivers                                   |
| `Outputs/llm_driver_risk_comparison.csv`  | Comparison of positive and negative aspects                              |
| `Outputs/llm_quality_by_segment.csv`      | Automation quality metrics by rating segment                             |
| `Outputs/llm_representative_evidence.csv` | Representative customer evidence for each theme                          |

## Technology

* Python
* Pandas and NumPy
* SQLite and SQL
* Anthropic Claude API
* Batch API processing
* Structured LLM outputs
* Prompt testing
* Evidence-grounding validation
* Human-in-the-loop review

## Data Source

This project uses the third-party Kaggle dataset **Sephora Products and Skincare Reviews (https://www.kaggle.com/datasets/nadyinky/sephora-products-and-skincare-reviews)**. The raw dataset and SQLite database are not included in this repository. Users should obtain the data directly from its original source and follow the source licensing requirements.

## Limitations

* The project uses historical reviews rather than real-time customer data.
* The 1,000-review sample was stratified for analysis and is not a population estimate.
* LLM-generated classifications are not equivalent to human-coded ground truth.
* The 124 routed cases require human review before final acceptance.
* The analysis identifies associations and recurring themes, not causal relationships.

## Disclaimer

This is an independent educational portfolio project using third-party public data. It is not affiliated with or endorsed by Sephora or Anthropic.
