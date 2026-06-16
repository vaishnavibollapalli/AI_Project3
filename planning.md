# TakeMeter Planning Document

## Community Choice

For this project, I chose the NBA Reddit community (r/nba). I selected this community because it contains a wide variety of discussion styles, including evidence-based basketball analysis, bold opinions, and emotional reactions to games and player performances. These differences make it an interesting classification task because the quality and style of discourse vary significantly across posts.

The NBA community is also a good fit because it is highly active and provides enough public comments to collect a balanced dataset of at least 200 examples. The distinctions between thoughtful analysis, unsupported opinions, and emotional reactions are meaningful to regular community members and reflect how basketball discussions are commonly evaluated.

---

## Label Definitions

### Analysis

A post is labeled Analysis if it uses evidence, statistics, basketball strategy, historical comparisons, or logical reasoning to support a claim.

Examples:

1. "Jokic averaged 29/13/8 against top-10 defenses this season, which explains why Denver's offense remained elite despite injuries."

2. "The Celtics switch-heavy defense works because every starter can effectively guard multiple positions."

---

### Hot Take

A post is labeled Hot Take if it expresses a strong opinion, prediction, or controversial claim without meaningful supporting evidence.

Examples:

1. "Anthony Edwards is already better than prime James Harden."

2. "The Thunder are going to win the next three championships."

---

### Reaction

A post is labeled Reaction if it primarily expresses emotion, excitement, frustration, surprise, or disappointment rather than making an argument.

Examples:

1. "WHAT A SHOT!!!"

2. "I can't believe we blew that lead again."

---

## Hard Edge Cases

The most difficult edge case is distinguishing between Analysis and Hot Take when a post includes a statistic but is still primarily expressing an unsupported opinion.

Example:

"LeBron is overrated because he only has four championships after twenty seasons."

This post contains evidence, but the statistic is being used rhetorically rather than as part of a detailed argument.

Decision Rule:

If the evidence is used to develop a logical explanation or argument, the post will be labeled Analysis.

If the evidence is only included to strengthen a provocative opinion without meaningful reasoning, the post will be labeled Hot Take.

---

## Data Collection Plan

Data will be collected from public comments and discussion threads on the r/nba subreddit.

Target label distribution:

| Label    | Target Count |
| -------- | ------------ |
| Analysis | 70           |
| Hot Take | 65           |
| Reaction | 65           |

Total examples: 200

Examples will be stored in a CSV file with the columns:

* text
* label
* notes

If one category becomes underrepresented, additional examples matching that category will be collected to maintain a balanced dataset. No label should account for more than 70% of the final dataset.

---

## Evaluation Metrics

The classifier will be evaluated using the following metrics:

* Accuracy
* Precision
* Recall
* F1 Score
* Confusion Matrix

Accuracy measures overall performance but does not reveal which labels are confused with one another. Precision, Recall, and F1 provide insight into how well the model performs for each label individually. A confusion matrix helps identify systematic classification errors and label boundary issues.

---

## Definition of Success

The classifier will be considered successful if it achieves:

* Overall accuracy of at least 75%
* Average F1 score of at least 0.70
* No individual label with an F1 score below 0.60

These thresholds would indicate that the model has learned meaningful distinctions between Analysis, Hot Take, and Reaction and could be useful as a lightweight discourse-quality classifier.

---

## AI Tool Plan

### Label Stress-Testing

Before large-scale annotation, ChatGPT will be used to generate borderline examples between Analysis and Hot Take. These examples will be used to refine label definitions and decision rules.

### Annotation Assistance

ChatGPT may be used to suggest labels for batches of examples. However, all labels will be manually reviewed and corrected before inclusion in the final dataset. Human review will remain the final source of truth.

### Failure Pattern Analysis

After evaluation, ChatGPT will be used to analyze misclassified examples and identify recurring patterns such as confusion between specific label pairs, emotional language, or short low-information posts. Any patterns suggested by the AI will be verified manually before being included in the final report.

---

## Expected Challenges

The most significant challenge is distinguishing Analysis from Hot Take when posts contain limited evidence. Some comments include a statistic or factual claim but still function primarily as an opinion. Maintaining consistent labeling criteria throughout the annotation process will be important for producing a reliable dataset and a useful classifier.
