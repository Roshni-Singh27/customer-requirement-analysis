# Unified Customer UGC Data Dictionary

| Field | Description | Type |
|---|---|---|
| review_id | Unique identifier for the review | String |
| source | Dataset/source from which the review originated | String |
| domain | Product/service domain | String |
| product_id | Product or item identifier when available | String |
| review_text | Original customer-generated text | String |
| rating | Customer rating when available | Numeric |
| timestamp | Review creation time when available | Datetime |
| helpful_votes | Number of helpful votes when available | Integer |
| language | Detected language | String |