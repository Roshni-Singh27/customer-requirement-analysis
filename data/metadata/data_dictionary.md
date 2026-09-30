# Unified Customer UGC Data Dictionary

## Dataset Level

The current intermediate dataset is based on the SemEval-2015 Task 12
restaurant and laptop review benchmark.

The dataset is represented at the **sentence-opinion annotation level**.
Therefore, one sentence may appear in multiple rows when it contains
multiple annotated opinions.

---

## Fields

| Field | Description | Type |
|---|---|---|
| review_id | Unique identifier of the original review | String |
| sentence_id | Unique identifier of the sentence within the review | String |
| domain | Review domain: restaurant or laptop | Categorical |
| sentence_text | Original customer-generated sentence text | String |
| target | Explicit opinion target/entity when available. For restaurant data, `NULL` may indicate that no explicit target was identified. Target is not applicable to the laptop annotation structure. | String / Nullable |
| category | Aspect category represented using the `ENTITY#ATTRIBUTE` format | Categorical / Nullable |
| polarity | Sentiment polarity associated with the annotated aspect | Categorical / Nullable |
| has_opinion_annotation | Indicates whether an opinion/polarity annotation is present | Boolean |
| has_aspect_category | Indicates whether an aspect category is present | Boolean |
| has_target | Indicates whether an explicit restaurant target is present | Boolean |

---

## Valid Polarity Values

The dataset uses the following sentiment labels:

- `positive`
- `negative`
- `neutral`

---

## Annotation Status

Records without opinion annotations are retained in the intermediate
dataset for auditability and broader user-generated-content processing.

Missing values in `target`, `category`, and `polarity` are therefore not
automatically treated as data errors.

---

## Category Format

Aspect categories follow the structure:

`ENTITY#ATTRIBUTE`

Examples include:

- `FOOD#QUALITY`
- `SERVICE#GENERAL`
- `RESTAURANT#GENERAL`
- `LAPTOP#DESIGN_FEATURES`
- `LAPTOP#OPERATION_PERFORMANCE`

---

## Dataset Representation

The data is stored at the annotation level rather than strictly at the
unique-sentence level.

Consequently:

- A single sentence can have multiple rows.
- Each row can represent a different opinion annotation.
- Exact duplicate annotation rows are removed during cleaning.
- Multiple distinct annotations for the same sentence are retained.

---

## Cleaning Summary

Initial parsed records: **4,163**

Final cleaned records: **4,161**

Redundant duplicate rows removed: **2**

Empty sentence records identified: **0**

Invalid polarity records identified: **0**

Invalid aspect-category format records identified: **0**


## Sentence-Level and Requirement Extraction Fields

| Field | Description | Type |
|---|---|---|
| sentence_id | Unique identifier of the sentence within the source dataset | String |
| sentence_text | Customer-generated sentence used for analysis | String |
| target | Explicit opinion target when available; `NULL` may represent an implicit/unspecified restaurant target | String / Nullable |
| category | SemEval aspect category associated with the opinion | String / Nullable |
| polarity | Sentiment polarity associated with the opinion | Categorical / Nullable |
| requirement_signal_type | Type of signal detected by the requirement extraction component | Categorical |
| prediction_confidence | Model confidence associated with the predicted requirement signal | Numeric |
| requirement_evidence_score | Score representing the strength of requirement-related evidence | Numeric |
| manual_requirement_label | Human validation label: `requirement`, `not_requirement`, or `uncertain` | Categorical |
| error_category | Category assigned during manual error analysis | Categorical / Nullable |

## Requirement Signal Types

The requirement extraction component uses the following signal categories:

- `direct_request` — explicit customer request or desired change
- `improvement_signal` — language indicating that a product/service could be improved
- `problem_or_missing` — a problem, limitation, or missing feature identified by the customer

## Manual Validation Labels

- `requirement` — sentence expresses a customer requirement or actionable need
- `not_requirement` — sentence does not represent a customer requirement
- `uncertain` — sentence cannot be confidently classified

## Error Categories

The manually identified extraction errors were categorized as:

- `positive_feedback` — customer expresses satisfaction or praise without requesting a change
- `preference_without_requirement` — customer expresses a preference without a clear actionable requirement
- `ambiguous` — sentence is difficult to classify confidently
- `general_opinion` — customer expresses an evaluation/opinion without a requirement
- `problem_without_actionable_request` — customer mentions a problem but does not clearly request a solution or change