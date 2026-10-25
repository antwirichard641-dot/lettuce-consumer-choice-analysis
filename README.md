# Consumer Choices for Hydroponic and Organic Lettuce: A Discrete-Choice Analysis

**Research area:** Consumer Behaviour · Agricultural Economics · Sustainable Food Systems · Applied Statistics · Data Science

**Project type:** Quantitative research and reproducible data analysis

**Primary methods:** Data cleaning, exploratory data analysis, conditional logit modelling, odds-ratio interpretation, participant-level bootstrap confidence intervals, and statistical visualization

---

## 1. Project Overview

Consumer preferences are important to the development and commercialization of alternative agricultural production systems and differentiated food products. As food production systems evolve, understanding how consumers respond to production methods, product labels, and prices can provide useful evidence for agricultural producers, marketers, researchers, and policymakers.

This project examines the associations between hydroponic production, organic labelling, price, and consumers' stated choices for lettuce. It uses a stated-choice dataset and a conditional logit model to investigate how these product attributes relate to the relative selection of alternatives within choice sets.

The analysis combines data preparation, exploratory checks, discrete-choice modelling, uncertainty estimation, and research communication in a reproducible notebook-based workflow.

The project is intended to demonstrate the application of statistical and data-science methods to an agricultural and food-market research question. It also illustrates how quantitative analysis can support evidence-based discussions of consumer preferences without overstating what the data can establish.

**Important interpretation note:** The dataset records stated choices in an experimental setting. The results therefore describe modelled associations with hypothetical choices, not necessarily observed purchases in actual markets.

## 2. Research Question

The central research question is:

> How are hydroponic production, organic labelling, and price associated with consumers' lettuce choices?

The analysis also examines the relative selection of lettuce product alternatives compared with the no-purchase alternative.

### Research objectives

1. Prepare and inspect the consumer-choice data for analysis.
2. Examine the structure of the choice experiment, including participants, choice sets, alternatives, and recorded selections.
3. Estimate a conditional logit model relating product attributes to relative selection odds.
4. Quantify uncertainty in the estimated odds ratios using participant-level bootstrap confidence intervals.
5. Visualize and communicate the principal findings.
6. Document methodological limitations and provide a reproducible analytical workflow.

## 3. Research Context and Significance

Consumer decisions about food products can reflect several attributes simultaneously. Price may influence affordability, while production-method information and product labels may affect how consumers evaluate alternatives.

Hydroponic production and organic labelling represent distinct product characteristics in this analysis. Their associations with stated choices are evaluated alongside price rather than in isolation.

The project contributes to practical agricultural data analysis by demonstrating how discrete-choice methods can be applied to a food-consumer dataset. The approach is relevant to research at the intersection of agricultural economics, consumer behaviour, food marketing, sustainable production, and applied statistics.

The analysis does not assume that one production system is inherently preferred or that a label automatically increases demand. Instead, the direction and uncertainty of each estimated association are evaluated using the fitted model.

## 4. Dataset and Analytical Structure

The project uses a stated-choice dataset concerning lettuce consumer preferences.

The cleaned dataset used in the analysis contains **4,752 rows and seven columns**:

| Variable | Description |
|---|---|
| `ID` | Participant identifier |
| `cset` | Choice-set identifier |
| `Alternative` | Alternative presented within a choice set |
| `Choice` | Indicator of whether the alternative was selected |
| `Hydro` | Indicator for hydroponic production |
| `Organic` | Indicator for organic labelling |
| `Price` | Price attribute recorded for the alternative |

The dataset contains 198 participants and 1,584 choice sets. Each choice set contains three alternatives, with exactly one alternative marked as selected.

The no-purchase alternative is represented by Alternative 3. In the cleaned dataset, this alternative has zero values for `Hydro`, `Organic`, and `Price`, consistent with its role as the no-purchase option in the analysis.

### Observed choice patterns

| Measure | Result |
|---|---:|
| Participants | 198 |
| Choice sets | 1,584 |
| Total alternative-level observations | 4,752 |
| Choice sets with a lettuce product selected | 1,153 (72.8%) |
| Choice sets with no purchase selected | 431 (27.2%) |

These descriptive figures summarize the recorded choices. They should not be interpreted as population-wide purchasing rates.

### Data access and attribution

The original dataset's source, citation, and redistribution permissions should be documented before distributing the data with this repository. Users reproducing the analysis should obtain the dataset from its authorized source and follow the relevant terms of use.

## 5. Analytical Methodology

The project follows a staged workflow designed to separate data preparation, model estimation, and research interpretation.

### 5.1 Data preparation

The first stage prepares the source data for analysis. The workflow includes checking the dataset structure, selecting the relevant variables, preparing the analysis-ready table, and saving the cleaned data for subsequent modelling.

The analytical dataset is organized at the alternative level, with observations grouped into choice sets. This structure is necessary because alternatives are evaluated relative to the other options available in the same choice situation.

### 5.2 Exploratory data analysis

Exploratory checks examine the dimensions and structure of the cleaned data, the number of participants and choice sets, the distribution of recorded choices, and the representation of the no-purchase alternative.

These checks help verify that the data structure is consistent with the intended discrete-choice analysis before fitting the model.

### 5.3 Conditional logit model

The project uses a conditional logit model to estimate how the included attributes are associated with relative selection within choice sets.

The fitted specification includes:

- `Product`: indicator distinguishing lettuce product alternatives from the no-purchase alternative.
- `Hydro`: indicator for hydroponic production.
- `Organic`: indicator for organic labelling.
- `Price`: the recorded price attribute.

The model accounts for the choice-set structure when estimating the relative selection associated with the included attributes.

The coefficient for an attribute represents its association with the log relative selection odds, conditional on the other included variables. Exponentiating a coefficient produces an odds ratio.

### 5.4 Odds ratios

Odds ratios provide a convenient way to communicate the fitted coefficients.

- An odds ratio above 1 indicates higher relative selection odds as the relevant indicator changes from 0 to 1, or as a continuous attribute increases by one unit.
- An odds ratio below 1 indicates lower relative selection odds.
- An odds ratio of 1 indicates no change in relative selection odds under the model.

For the binary attributes, interpretation depends on the coding of the variable. For price, the numerical meaning of a one-unit increase depends on the price units used in the dataset.

Odds ratios are not percentage-point changes in the probability of choosing an alternative. They should not be described as causal effects.

### 5.5 Participant-level bootstrap uncertainty

Participant-level bootstrap resampling was used to estimate 95% confidence intervals for the odds ratios. The procedure resamples participants rather than treating every alternative-level observation as an independent participant.

The reported analysis used 200 successful bootstrap replications. This provides an exploratory assessment of uncertainty, although a larger number of replications could improve the numerical stability of percentile confidence intervals.

## 6. Results

The following estimates are from the fitted conditional logit model and the participant-level bootstrap analysis.

| Model term | Odds ratio | 95% participant-bootstrap CI |
|---|---:|---:|
| Product vs. no purchase | 3.405 | 2.458–4.961 |
| Hydroponic production | 0.852 | 0.720–1.047 |
| Organic labelling | 2.373 | 1.974–2.780 |
| Price | 0.546 | 0.494–0.590 |

### 6.1 Organic labelling

Organic labelling had an estimated odds ratio of **2.373**, with a 95% participant-bootstrap confidence interval of **1.974–2.780**.

This positive association indicates that the organic-labelled attribute was associated with higher relative selection odds in the fitted model, holding the other included attributes constant.

The confidence interval lies above 1, supporting a positive association within the model and dataset. This result does not establish that organic labelling causes an increase in actual purchasing.

### 6.2 Price

Price had an estimated odds ratio of **0.546**, with a 95% participant-bootstrap confidence interval of **0.494–0.590**.

The negative association indicates that higher prices were associated with lower relative selection odds in the fitted model, holding the other included attributes constant.

The confidence interval lies below 1. The size of the effect should be interpreted in relation to the price units and coding used in the dataset.

### 6.3 Hydroponic production

Hydroponic production had an estimated odds ratio of **0.852**, with a 95% participant-bootstrap confidence interval of **0.720–1.047**.

The point estimate is below 1, but the confidence interval includes 1. The estimate is therefore inconclusive: the analysis does not provide clear evidence of either a positive or negative association at the conventional 95% confidence-interval level.

It would be inappropriate to conclude from this result alone that consumers prefer or reject hydroponically produced lettuce.

### 6.4 Product alternatives compared with no purchase

The product indicator had an estimated odds ratio of **3.405**, with a 95% participant-bootstrap confidence interval of **2.458–4.961**.

This estimate indicates higher relative selection odds for a lettuce product alternative compared with the no-purchase alternative under the fitted model and its variable coding.

This comparison provides context for interpreting the product attributes. It is not a direct estimate of market demand or the probability that a consumer will buy lettuce.

## 7. Main Findings at a Glance

The model results support three principal observations:

1. **Organic labelling was positively associated with relative selection odds.** Its confidence interval was entirely above 1.
2. **Price was negatively associated with relative selection odds.** Its confidence interval was entirely below 1.
3. **The estimated association for hydroponic production was inconclusive.** Its confidence interval included 1.

The product indicator also showed higher relative selection odds for lettuce alternatives than for the no-purchase alternative.

Taken together, these findings demonstrate how product attributes can be evaluated jointly within a discrete-choice framework. They should be understood as evidence from this dataset and model rather than universal conclusions about lettuce consumers.

## 8. Research Limitations

Several limitations should guide interpretation.

### Stated-choice data

The analysis uses hypothetical stated choices. Responses in an experimental setting may differ from actual purchasing behaviour, particularly when real financial costs and market conditions are involved.

### Association rather than causation

The fitted model estimates associations between attributes and relative selection odds. These estimates should not automatically be interpreted as causal effects.

### Uncertainty in the hydroponic estimate

The hydroponic confidence interval includes an odds ratio of 1. Consequently, the estimated negative association is not conclusive under the reported interval-based assessment.

### Functional form of price

The model assumes a linear effect of price on the log-odds scale. If the actual price relationship is nonlinear, this specification may not capture every aspect of consumer response.

### Generalizability

The results may not generalize beyond the participants, product attributes, and choice scenarios represented in the dataset.

### Bootstrap replication count

The participant-level bootstrap used 200 successful replications. Additional replications could improve the stability of the percentile confidence intervals.

### Dataset provenance and experimental context

Interpretation depends on the original study's sampling, experimental design, variable definitions, and data-collection context. Those details should be consulted in the original dataset documentation before drawing broader conclusions.

## 9. Reproducibility and Project Organization

The repository contains three notebooks that separate the analytical stages.

| Notebook | Purpose |
|---|---|
| `01_Consumer_Choice_Data_Preparation_and_Exploration.ipynb` | Data preparation, structural checks, and exploratory analysis |
| `02_Consumer_Choice_Modeling_Hydroponic_Organic_Lettuce.ipynb` | Conditional logit estimation, odds ratios, and participant-bootstrap confidence intervals |
| `03_Results_Visualization_and_Research_Conclusions.ipynb` | Results visualization, findings summary, limitations, and research conclusion |

### Recommended execution order

1. Obtain the dataset from its authorized source.
2. Run Notebook 1 to prepare and inspect the analysis data.
3. Run Notebook 2 to estimate the model and generate the model-results file.
4. Run Notebook 3 to visualize the results and prepare the findings and conclusion outputs.

Required input files must be placed in the locations expected by the notebooks. Where necessary, update file paths to match the execution environment.

A successful run requires more than having the notebooks stored on GitHub: the input data must be available, dependencies must be installed, and the cells must execute in order without relying on variables from an earlier interactive session.

## 10. Expected Research Outputs

The analysis workflow produces the following research artifacts:

- `lettuce_choice_model_results.csv` — model coefficients, odds ratios, and confidence intervals.
- `lettuce_choice_odds_ratios.png` — forest plot of odds ratios and confidence intervals.
- `lettuce_choice_findings_summary.csv` — concise table of principal findings and interpretations.
- `lettuce_choice_research_limitations.csv` — documented study limitations.
- `lettuce_choice_research_conclusion.md` — written research conclusion.
- `lettuce_consumer_choice_clean.csv` — cleaned analysis dataset, subject to source permissions and repository sharing decisions.

These outputs should be included in the repository only after their contents, filenames, provenance, and permissions have been checked.

## 11. Tools and Technical Skills Demonstrated

This project demonstrates the use of a notebook-based analytical workflow for an agricultural consumer-research question.

The work includes:

- Python-based data preparation and tabular data handling.
- Exploratory data analysis and structural validation.
- Discrete-choice modelling using a conditional logit specification.
- Interpretation of regression coefficients and odds ratios.
- Participant-level bootstrap uncertainty estimation.
- Statistical visualization and confidence-interval interpretation.
- Research documentation, limitations reporting, and reproducible workflow design.
- Version-controlled organization of analytical code and outputs.

The project illustrates the application of quantitative methods to a real research question rather than serving only as a software demonstration.

## 12. Conclusion

This project examined how hydroponic production, organic labelling, and price were associated with consumers' stated choices for lettuce.

Organic labelling was positively associated with relative selection odds, while price was negatively associated with relative selection odds. The estimated association for hydroponic production was negative but inconclusive because its participant-bootstrap confidence interval included 1. Lettuce product alternatives also had higher relative selection odds than the no-purchase alternative.

The analysis demonstrates the value of conditional logit modelling and participant-level bootstrap confidence intervals for studying consumer choice data. At the same time, the stated-choice design, model specification, and uncertainty of some estimates limit the conclusions that can be drawn.

The central conclusion is that the results provide evidence of associations within the fitted model and dataset, not proof of causal effects or a guarantee of actual market behaviour.

## 13. Responsible Use and Citation

If you reuse this analysis, cite the original dataset and study using the source's recommended citation. Check its terms before redistributing data, and distinguish reproduced findings from any new analyses.

This repository is intended to support transparent research communication, methodological learning, and reproducible agricultural data analysis.

---

**Project focus:** Consumer choice · Lettuce · Hydroponic production · Organic labelling · Price · Conditional logit · Agricultural data science
