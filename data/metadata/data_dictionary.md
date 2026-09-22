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