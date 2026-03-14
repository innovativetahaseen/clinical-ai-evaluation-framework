# 🧠 Clinical AI Evaluation Framework

A lightweight evaluation framework for analyzing **reliability and trustworthiness of clinical AI pipelines** that extract structured entities from medical charts.

This project was developed as part of the **HiLabs Workshop: Building Evals and Reliability Layers for Generative AI in Healthcare**.

---

# 📌 Overview

Modern healthcare AI systems typically use pipelines that include:

- OCR processing of scanned medical charts
- Clinical NLP entity extraction
- Structured medical data generation

However, these pipelines can introduce errors in:

- Entity classification
- Assertion detection
- Temporal reasoning
- Subject attribution

This project implements a **rule-based evaluation framework** to measure reliability across these dimensions.

---

# 🎯 Objectives

The framework evaluates AI extraction outputs and helps identify:

- Where the system performs well
- Where errors occur frequently
- Which reasoning dimensions are unreliable

This helps design **guardrails for safer clinical AI deployment**.

---

# ⚙️ Evaluation Metrics

The framework evaluates outputs using the following metrics.

## 1️⃣ Entity Type Error Rate

Measures incorrect classification across:

- MEDICINE
- PROBLEM
- PROCEDURE
- TEST
- VITAL_NAME
- IMMUNIZATION
- MEDICAL_DEVICE
- MENTAL_STATUS
- SDOH
- SOCIAL_HISTORY

---

## 2️⃣ Assertion Error Rate

Evaluates correctness of entity assertions:

- POSITIVE
- NEGATIVE
- UNCERTAIN

---

## 3️⃣ Temporality Error Rate

Checks temporal reasoning accuracy:

- CURRENT
- CLINICAL_HISTORY
- UPCOMING
- UNCERTAIN

---

## 4️⃣ Subject Attribution Error

Determines whether the entity belongs to:

- PATIENT
- FAMILY_MEMBER

---

## 5️⃣ Event Date Accuracy

Measures correctness of temporal event extraction.

---

## 6️⃣ Attribute Completeness

Evaluates whether required attributes are present in extracted entities.

---

# 📂 Repository Structure

```
clinical-ai-evaluation-framework
│
├── output/
│   ├── file_1.json
│   ├── file_2.json
│   └── ...
│
├── test.py
├── report.md
└── README.md
```

---

# 📦 Dataset

The dataset contains **OCR-processed clinical charts and extracted entities**.

Each test folder contains:

```
test_data/
 ├── folder_1/
 │   ├── folder_1.json
 │   └── folder_1.md
```

The JSON file contains extracted clinical entities used for evaluation.

---

# ▶️ How to Run

Run evaluation for a single chart:

```
python test.py input.json output.json
```

Example:

```
python test.py test_data/chart_01/chart_01.json output/chart_01.json
```

---

# ⚡ Batch Processing (All Charts)

Run evaluation for all folders automatically:

```
for dir in test_data/*; do
  name=$(basename "$dir")
  python test.py "$dir/$name.json" "output/$name.json"
done
```

This will generate **evaluation reports for all charts automatically**.

---

# 📊 Output Format

Each output JSON file contains a reliability evaluation report.

Example:

```json
{
  "file_name": "chart_01.json",
  "entity_type_error_rate": {},
  "assertion_error_rate": {},
  "temporality_error_rate": {},
  "subject_error_rate": {},
  "event_date_accuracy": 0.85,
  "attribute_completeness": 0.92
}
```

---

# 🔎 Key Observations

Common weaknesses in clinical extraction pipelines include:

- Temporality misclassification
- Missing entity attributes
- Incorrect subject attribution
- Ambiguous assertions

---

# 🛡️ Proposed Guardrails

To improve reliability:

1. Confidence-based filtering  
2. Temporal reasoning validation  
3. Entity schema validation  
4. Cross-entity consistency checks  

---

# 🚀 Future Improvements

- LLM-based error classification  
- Visualization dashboards for error heatmaps  
- Automated guardrail generation  
- Integration with real-time clinical AI pipelines  

---

# 👨‍💻 Author

