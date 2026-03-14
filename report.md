
# Clinical AI Reliability Evaluation

## Objective
This project evaluates reliability of clinical AI pipelines that extract structured entities from OCR medical charts.

## Metrics
- Entity Type Classification
- Assertion Detection
- Temporality Reasoning
- Subject Attribution
- Event Date Accuracy
- Attribute Completeness

## Key Observations
Common weaknesses in clinical extraction systems include:
- Temporality misclassification
- Missing attributes in entities
- Incorrect subject attribution

## Suggested Guardrails
1. Confidence threshold filtering
2. Temporal reasoning validation
3. Schema completeness validation
