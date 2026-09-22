Dataset selection: SemEval-2015 Task 12 selected as the primary benchmark dataset for the review-based component.

Primary domains:
- Laptop reviews
- Restaurant reviews

SemEval-2014 Task 4: Secondary/reference benchmark for sentence-level ABSA comparison.

Requirement prioritization labels:
To be developed and experimentally validated.


## Acquired Dataset

### SemEval-2015 Restaurants Training Data

File:
`ABSA-15_Restaurants_Train_Final.xml`

Official dataset:
SemEval-2015 Task 12 - Restaurants Train Data

Original source:
SemEval-2015 Task 12 / META-SHARE

Acquisition source:
Public secondary copy used because the original META-SHARE download link was unavailable at the time of acquisition.

SHA-256:

`813C3BF02CFDCE98E1ECCA93ECA46E0123EBD8A2848A506D18BD3C1BE9037DF`

Local path:
`data/raw/semeval2015/ABSA-15_Restaurants_Train_Final.xml`

Redistribution:
Raw dataset should not be committed to the public repository unless the applicable dataset terms explicitly permit redistribution.


### SemEval-2015 Laptops Training Data

File:
`ABSA-15_Laptops_Train_Data.xml`

Official dataset:
SemEval-2015 Task 12 - Laptops Train Data

Original source:
SemEval-2015 Task 12 / META-SHARE

Acquisition source:
Public secondary copy used because the original META-SHARE download link was unavailable at the time of acquisition.

SHA-256:

`0E9DAA0577F7546F7753400E2D88A464D4FBFF5B3C47AE94C32A298A9953ADA`

Local path:
`data/raw/semeval2015/ABSA-15_Laptops_Train_Data.xml`

Redistribution:
Raw dataset should not be committed to the public repository unless the applicable dataset terms explicitly permit redistribution.

## Processing and Reproducibility

The acquired SemEval-2015 Task 12 XML files were processed using the
notebook:

`notebooks/01_data_collection.ipynb`

### Processing workflow

1. Load the SemEval-2015 restaurant and laptop XML files.
2. Parse reviews, sentences, and opinion annotations.
3. Combine the restaurant and laptop records into a unified dataframe.
4. Validate text completeness.
5. Validate sentiment polarity labels.
6. Validate aspect-category format.
7. Inspect category consistency by domain.
8. Identify exact duplicate annotation records.
9. Remove only redundant exact duplicate rows.
10. Save the cleaned intermediate dataset locally.

### Cleaning Result

Initial parsed records: **4,163**

Records involved in exact duplicate groups: **4**

Redundant duplicate rows removed: **2**

Final cleaned records: **4,161**

Final domain distribution:

- Laptop: **2,314**
- Restaurant: **1,847**

The cleaned intermediate dataset is generated locally at:

`data/intermediate/semeval2015/semeval2015_combined_cleaned.csv`

The derived dataset is excluded from version control through `.gitignore`.
This allows the dataset to be regenerated from the locally acquired source
data using the data-collection notebook.

### Important Annotation Handling

Missing values were not globally removed.

The SemEval annotation structure contains sentences without opinion
annotations, and target annotations are domain-dependent. Therefore,
missing `target`, `category`, or `polarity` values are interpreted according
to the annotation structure rather than automatically treated as invalid
records.