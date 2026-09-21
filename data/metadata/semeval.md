# SemEval Dataset Documentation

## Research Project

Customer Requirement Analysis Using User Generated Content

## Research Objective

Develop an NLP-driven framework for extracting, analyzing, and prioritizing customer requirements from user-generated content such as reviews, surveys, and feedback.

## Role of SemEval Dataset

The SemEval ABSA datasets will be investigated as benchmark datasets for aspect extraction, aspect categorization, and aspect-level sentiment analysis.

The SemEval datasets do not directly provide customer requirement priority labels. Therefore, requirement prioritization will be treated as a separate research component.

## Candidate Dataset

SemEval-2014 Task 4 - Aspect Based Sentiment Analysis (ABSA)

### Domains

- Laptop reviews
- Restaurant reviews

### Main Tasks

1. Aspect term extraction
2. Aspect term polarity
3. Aspect category detection
4. Aspect category polarity

The restaurant dataset contains aspect categories and category-level polarity, while the laptop dataset contains aspect terms and their polarities.

## Data Format

The SemEval-2014 datasets are provided in XML format.

Example structure:

- sentence ID
- review sentence/text
- aspect term
- sentiment polarity
- aspect term character offsets
- aspect category
- aspect category polarity

## Sentiment Labels

- positive
- negative
- neutral
- conflict

## Research Relevance

The dataset can support the following components of the proposed framework:

- Customer aspect identification
- Customer sentiment analysis
- Aspect-level opinion analysis
- Requirement/category extraction
- Benchmark evaluation of NLP models

## Limitation

SemEval does not directly contain a customer requirement priority label.

Therefore, a separate methodology will be required to convert extracted customer requirements into priority levels.

Possible factors for future investigation include:

- Requirement frequency
- Sentiment polarity
- Sentiment severity
- Customer rating
- Number of mentions
- Helpfulness signals
- Cross-review recurrence

These factors must be validated experimentally before being used in the final prioritization model.

## Official Sources

SemEval-2014 Task 4:
https://alt.qcri.org/semeval2014/task4/

SemEval-2014 Data and Tools:
https://alt.qcri.org/semeval2014/task4/index.php?id=data-and-tools

SemEval-2015 Task 12:
https://alt.qcri.org/semeval2015/task12/

## Data Usage

The official SemEval documentation states that the data were collected manually and made available within the scope of fair use and the terms and conditions of the data providers.

Dataset licensing/usage conditions must be reviewed before redistributing raw data in the GitHub repository.

## Status

Dataset selection: Under evaluation

SemEval role: Benchmark dataset

Requirement prioritization labels: To be developed/validated