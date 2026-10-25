# Consumer Choices for Hydroponic and Organic Lettuce: A Discrete-Choice Analysis

**Research area:** Agricultural Economics · Consumer Behaviour · Food Systems · Applied Econometrics · Sustainable Agriculture

**Project type:** Quantitative consumer-choice research

**Primary methods:** Data preparation, exploratory data analysis, conditional logistic regression, odds-ratio interpretation, and statistical visualisation

**Programming environment:** Python and Jupyter Notebook

---

## 1. Project Overview

This research project investigates how production method, organic status, and price are associated with consumer stated choices for lettuce. Using a discrete-choice dataset, the analysis examines the relative importance of product attributes when consumers select among lettuce alternatives or choose not to purchase.

The project sits at the intersection of agricultural economics, consumer behaviour, food marketing, and sustainable food production. Understanding how consumers respond to product attributes can help researchers investigate the market positioning of alternative production systems and the potential role of price and product differentiation in food choices.

The analysis focuses on three principal attributes:

- **Hydroponic production:** whether the lettuce alternative is identified as hydroponically produced.
- **Organic status:** whether the alternative carries the organic attribute.
- **Price:** the stated price associated with each alternative.

The dataset includes a no-purchase alternative, allowing the analysis to examine product selection in relation to the option of not purchasing.

The project is organised to support transparent data handling, statistical modelling, interpretation of results, and reproducible research. Results are interpreted as evidence about stated preferences within the analysed dataset, not as direct measurements of actual purchasing behaviour.

## 2. Research Motivation

Agricultural producers and food-market stakeholders operate in an environment where production systems, sustainability attributes, certification, and prices may influence consumer perceptions and choices.

Hydroponic production can differ from conventional soil-based cultivation in its production methods and resource-management characteristics. Organic status represents a separate product attribute that may influence how consumers evaluate food. Price introduces an economic consideration that can affect the attractiveness of competing alternatives.

However, the presence of a product attribute does not automatically demonstrate that consumers value it positively. Its estimated association with choice must be evaluated empirically, alongside uncertainty and other attributes.

This project therefore uses a quantitative discrete-choice framework to examine how hydroponic production, organic status, and price relate to selection outcomes. The intention is to provide a transparent analytical workflow that can be reviewed, reproduced, and extended as the research develops.

## 3. Research Aim

The main aim is to analyse the relationship between lettuce product attributes and consumer stated choices using discrete-choice modelling.

### Specific objectives

1. Prepare and document a structured dataset of consumer choice observations.
2. Examine the distribution of participants, choice sets, alternatives, attributes, and observed selections.
3. Estimate the associations between hydroponic production, organic status, price, and alternative selection.
4. Compare product-selection outcomes with the availability of a no-purchase option.
5. Translate model coefficients into interpretable odds ratios and uncertainty intervals.
6. Communicate the findings through clear tables and figures.
7. Document methodological assumptions, limitations, and requirements for reproducibility.

## 4. Research Questions

The analysis is organised around the following questions:

**RQ1.** How is hydroponic production associated with the probability of selecting a lettuce alternative, conditional on the other attributes included in the model?

**RQ2.** How is organic status associated with consumer stated choice?

**RQ3.** What is the relationship between price and the likelihood that an alternative is selected?

**RQ4.** How do product alternatives compare with the no-purchase alternative within the observed choice sets?

**RQ5.** How precisely can the estimated relationships be established, and what limitations affect their interpretation?

These questions concern statistical associations in the observed stated-choice data. They do not, by themselves, establish causal effects or predict actual market demand.

## 5. Dataset Description

The cleaned analytical dataset is named `lettuce_consumer_choice_clean.csv`.

The recorded dataset dimensions are:

| Dataset characteristic | Recorded value |
|---|---:|
| Observations | 4,752 |
| Variables | 7 |
| Participants | 198 |
| Choice sets | 1,584 |
| Alternatives per choice set | 3 |
| Selected alternatives per choice set | 1 |

The dataset therefore contains 4,752 alternative-level observations across 1,584 choice sets. Each choice set contains three alternatives, with one recorded selection.

These counts describe the dataset used in the earlier analysis and should be rechecked when the notebook is rerun.

### Variables

| Variable | Description | Analytical role |
|---|---|---|
| `ID` | Participant identifier | Identifies participants and supports participant-level grouping |
| `cset` | Choice-set identifier | Identifies alternatives presented within a choice set |
| `Alternative` | Alternative identifier | Distinguishes the alternatives within a choice set |
| `Choice` | Selection indicator | Identifies the alternative selected by the participant |
| `Hydro` | Hydroponic attribute indicator | Represents the hydroponic production attribute |
| `Organic` | Organic attribute indicator | Represents the organic attribute |
| `Price` | Alternative price | Represents the stated price associated with an alternative |

The precise coding and units of each variable should be verified against the original questionnaire, codebook, or source dataset before substantive interpretation.

### No-purchase alternative

The analysis treats Alternative 3 as the no-purchase option. In the cleaned dataset, its attribute values were recorded as `Price = 0`, `Hydro = 0`, and `Organic = 0`.

This coding is important for model specification and interpretation. A zero price for the no-purchase alternative represents the absence of a purchase rather than necessarily representing a market-priced lettuce product.

The reference category and interpretation of coefficients must be consistent with the actual model formula used in the notebook.

## 6. Data Preparation and Quality Assurance

The project includes a dedicated data-preparation and exploratory-analysis notebook.

The intended preparation workflow includes:

1. Loading the source data and recording the original data dimensions.
2. Inspecting column names, variable types, and the structure of the observations.
3. Selecting and documenting the variables required for the choice analysis.
4. Checking missing values, duplicated records, and identifier consistency.
5. Verifying the number of participants, choice sets, and alternatives.
6. Checking that each choice set has the expected number of alternatives.
7. Checking that each choice set contains exactly one selected alternative.
8. Reviewing the coding of product attributes and the no-purchase option.
9. Saving the cleaned analytical dataset and relevant validation outputs.

These checks should be implemented and confirmed through the notebook. Their inclusion in this README describes the intended quality-assurance process; it does not imply that every check has already been independently passed.

### Data provenance

The original dataset was identified as `AE_hydro_org.csv`. The cleaned dataset was saved as `lettuce_consumer_choice_clean.csv`.

The raw-to-clean transformation should be documented with the source location, variable mapping, exclusion rules, recoding decisions, and any other processing steps. The original source data and the cleaned analytical file should not be treated as interchangeable.

Where redistribution of the original dataset is restricted or its licence is unclear, the repository should provide appropriate source attribution and access instructions rather than publish data without permission.

## 7. Exploratory Data Analysis

Exploratory analysis is used to establish the structure of the data before interpreting the regression estimates.

The planned analysis includes:

- Participant and choice-set counts.
- Distribution of alternatives across choice sets.
- Frequency of selected and unselected alternatives.
- Distribution of the hydroponic and organic indicators.
- Summary statistics for price.
- Inspection of the no-purchase option.
- Visualisations of choice outcomes and attribute distributions.

Exploratory results should be interpreted in the context of the choice-set design. Alternative-level observations are not necessarily independent because alternatives are grouped within choice sets and multiple choice sets may come from the same participant.

Descriptive patterns are useful for understanding the dataset, but they do not replace the conditional choice model.

## 8. Statistical Methodology

### Conditional logistic regression

The primary reported model is a conditional logistic regression designed for grouped choice data. The model evaluates the relative selection of alternatives within choice sets using their observed attributes.

A general representation of the conditional choice probability is:

\[
P_{ij} =
\frac{\exp(V_{ij})}
{\sum_{k \in C_j}\exp(V_{kj})}
\]

where:

- \(P_{ij}\) is the probability that alternative \(i\) is selected in choice set \(j\).
- \(C_j\) is the set of available alternatives in choice set \(j\).
- \(V_{ij}\) is the systematic utility component for alternative \(i\).

A representative linear utility specification is:

\[
V_{ij} =
\beta_H Hydro_{ij}
+\beta_O Organic_{ij}
+\beta_P Price_{ij}
\]

The exact specification must be confirmed from the executable notebook. If the model includes additional terms, alternative-specific indicators, interactions, or a different reference structure, the equation and its interpretation should be updated accordingly.

### Interpretation of coefficients

- A positive coefficient indicates higher relative utility, and hence higher relative selection odds, for a one-unit increase in that attribute, holding the other included terms constant.
- A negative coefficient indicates lower relative selection odds for a one-unit increase in the attribute.
- The magnitude depends on how the variable is coded and measured.
- Statistical uncertainty should be considered alongside coefficient direction and magnitude.

For binary attributes, the odds ratio is commonly calculated as:

\[
OR = \exp(\beta)
\]

An odds ratio above 1 indicates higher relative odds of selection for the coded attribute, while an odds ratio below 1 indicates lower relative odds. An odds ratio should not be described directly as a percentage-point change in choice probability.

### Price interpretation

The price coefficient depends on the price unit and coding used in the dataset. Its interpretation should therefore specify the actual price unit and the size of the change being evaluated.

The no-purchase alternative requires particular care because its price is coded as zero. This is not necessarily equivalent to observing a market-priced product at zero cost.

### Uncertainty and statistical inference

Model interpretation should consider confidence intervals, standard errors, and the assumptions underlying the estimator.

A confidence interval for an odds ratio that includes 1 does not establish a clear directional association at the corresponding confidence level. Conversely, an interval that excludes 1 provides evidence of an association under the fitted model and its inferential assumptions; it does not prove causality.

The statistical significance threshold and confidence level should be explicitly reported in the final results.

## 9. Participant-Level Bootstrap Analysis

Earlier project outputs reported a participant-level bootstrap with 200 replications for uncertainty estimation.

A participant-level bootstrap is intended to account for the fact that one participant may contribute multiple choice sets. In each replication, participants should be resampled as clusters, with all relevant choice-set observations for each sampled participant retained.

The implementation should ensure that duplicated participant draws receive unique bootstrap identifiers and that choice-set identifiers do not accidentally merge observations from different sampled copies.

The following details should be reported in the final analysis:

- Number of bootstrap replications.
- Unit of resampling.
- Treatment of repeated participant draws.
- Handling of failed or non-convergent model fits.
- Method used to calculate confidence intervals.
- Number of successful replications.

The previously reported 200-replication procedure should be treated as provisional until its code and outputs are reviewed. The stability of percentile-based confidence intervals should also be assessed before the bootstrap results are presented as final.

## 10. Previously Reported Model Estimates

The following odds ratios and confidence intervals were reported in an earlier analysis. They are included as preliminary results for transparency and should be regenerated from the committed notebooks before being treated as final.

| Model term | Reported odds ratio | Reported 95% confidence interval | Preliminary interpretation |
|---|---:|---:|---|
| Product versus no purchase | 3.405 | 2.458–4.961 | Higher reported relative selection odds for the product alternative under the earlier model |
| Hydroponic attribute | 0.852 | 0.720–1.047 | Direction is uncertain because the interval includes 1 |
| Organic attribute | 2.373 | 1.974–2.780 | Higher reported relative selection odds associated with the organic attribute |
| Price | 0.546 | 0.494–0.590 | Lower reported relative selection odds as price increases, subject to the price coding and unit |

**Important:** These estimates are carried forward from earlier project notes. They have not been independently reproduced in this README. Their exact interpretation depends on the fitted model formula, reference categories, price unit, and confidence-interval procedure.

The term “Product versus no purchase” requires particular scrutiny: it should be included in the final model-results table only if the fitted model explicitly estimates and identifies that contrast.

## 11. Preliminary Interpretation

Subject to verification of the model specification and uncertainty estimates, the earlier results suggest three patterns worth investigating further.

### Organic status

The previously reported odds ratio for organic status was above 1, with a confidence interval excluding 1. This is consistent with a positive association between the organic attribute and relative selection odds in the earlier fitted model.

This result should not be generalised to all consumers or actual retail purchases without further evidence.

### Hydroponic production

The previously reported confidence interval for the hydroponic attribute included 1. The estimate therefore does not provide sufficiently clear evidence of a directional association at the corresponding confidence level.

The appropriate conclusion is that the association remains uncertain, rather than that consumers necessarily prefer or reject hydroponic lettuce.

### Price

The earlier model reported an odds ratio below 1 for price. If the price variable is coded as expected and its units are confirmed, this would be consistent with lower relative selection odds at higher prices.

The size of the price association should be interpreted using the actual price scale and the final model specification.

### Product selection versus no purchase

The earlier output reported higher selection odds for a product alternative relative to no purchase. This contrast should only be discussed as a separate model estimate after the underlying parameterisation and reference category have been verified.

## 12. Figures and Research Outputs

The repository is organised to separate source data, analytical outputs, findings, and visualisations.

### `datasets/`

Contains the cleaned analytical dataset and dataset documentation.

### `results/`

Contains model results, summary tables, and documented analytical outputs, including:

- `lettuce_choice_model_results.csv`
- `lettuce_choice_findings_summary.csv`
- `lettuce_choice_research_limitations.csv`

The file contents and column definitions should be checked to ensure that each output accurately reflects the final model run.

### `findings/`

Contains the written interpretation and conclusions, including:

- `lettuce_choice_research_conclusion.md`

Written findings should agree with the model estimates and their uncertainty intervals.

### `figures/`

Contains plots generated from the analysis, including:

- `lettuce_choice_odds_ratios.png`

Figures should have informative titles, labelled axes, clear confidence intervals where applicable, and notes identifying the model and reference categories.

### Jupyter notebooks

The repository contains three intended analytical notebooks:

1. **Data Preparation and Exploration** — documents the cleaned data, quality checks, and descriptive analysis.
2. **Consumer Choice Modelling** — fits the conditional logistic regression and estimates uncertainty.
3. **Results Visualization and Research Conclusions** — communicates the model estimates, figures, and evidence-based interpretation.

Notebook filenames and locations should be verified against the actual repository. Each notebook should clearly identify its inputs, outputs, dependencies, and execution order.

## 13. Reproducibility and Research Transparency

The project is intended to support independent review and reproducible analysis.

The following standards should be followed:

- Use descriptive, consistent filenames.
- Keep data preparation and modelling steps documented.
- Identify the source and licence of each dataset.
- State variable definitions, coding decisions, and units.
- Record software dependencies and relevant package versions.
- Use a documented random seed for bootstrap or other randomised procedures.
- Report failed model fits and material changes to the analytical procedure.
- Generate tables and figures from the analysis code rather than manually altering reported values.
- Keep the written conclusions consistent with the final verified model outputs.
- Avoid committing private, restricted, or personally identifiable information.
- Document any changes to the dataset or model specification.

A fresh execution of the notebooks should reproduce the main tables and figures, subject to documented software and numerical differences.

## 14. Limitations

The following limitations are relevant to the interpretation of the project.

**Stated versus actual behaviour.** The dataset records stated choices. Such choices may not correspond exactly to real purchasing behaviour under real-world budget constraints and market conditions.

**Sampling and representativeness.** The available information does not, by itself, establish that the 198 participants represent a broader consumer population. External generalisation should therefore be cautious.

**Model specification.** Estimates depend on the selected variables, coding, reference categories, and functional form. Alternative specifications may yield different estimates.

**Dependence within participants.** Multiple choice sets from the same participant create dependence that should be addressed appropriately in uncertainty estimation.

**Price coding.** The units, range, and interpretation of price must be documented. The zero-coded no-purchase option requires special consideration.

**Uncertainty in the hydroponic estimate.** The earlier reported confidence interval included an odds ratio of 1, so a clear directional conclusion is not warranted from that estimate alone.

**Unverified reproducibility.** The previously reported estimates and bootstrap intervals require validation against the final notebook code and outputs.

**Causal interpretation.** The analysis is observational with respect to the recorded choice attributes as analysed here. Unless the study design and identification assumptions justify causal inference, findings should be described as associations.

These limitations are part of responsible interpretation and provide a basis for improving the analysis.

## 15. Potential Extensions

Future work may consider the following extensions where the dataset and study design support them:

1. Compare alternative model specifications and assess sensitivity to coding decisions.
2. Investigate participant heterogeneity if relevant demographic or preference variables are available and appropriately documented.
3. Estimate and communicate predicted choice probabilities for clearly defined scenarios.
4. Evaluate willingness-to-pay measures only if the model specification, price scale, and assumptions support them.
5. Compare conditional logit with alternative discrete-choice models where justified.
6. Improve uncertainty estimation and report bootstrap convergence and sensitivity.
7. Link stated preferences to observed purchasing behaviour if suitable data become available.
8. Examine whether findings differ across relevant consumer groups, provided the sample size and data support such analysis.

These are possible extensions, not completed analyses.

## 16. Conclusion

This project develops a quantitative framework for examining how hydroponic production, organic status, and price are associated with stated consumer choices for lettuce.

The earlier reported estimates suggest a positive association for organic status, a negative association for price, and uncertainty surrounding the hydroponic attribute. These patterns are preliminary and require verification through execution of the committed analysis notebooks.

The principal contribution of the project is its structured approach to agricultural consumer-choice research: a documented dataset, a discrete-choice modelling framework, interpretable statistical outputs, visual communication, and explicit attention to uncertainty and research limitations.

The project will be considered reproducible when the source data and transformations are documented, the notebooks run successfully in sequence, the model outputs can be regenerated, and the final conclusions agree with the verified estimates.

## 17. Repository Navigation

- **`datasets/`** — cleaned data and dataset documentation.
- **`results/`** — model estimates, summary tables, and analytical outputs.
- **`findings/`** — written findings, conclusions, and research limitations.
- **`figures/`** — visualisations generated by the analysis.
- **Jupyter notebooks** — data preparation, model estimation, and reporting workflow.

For questions about data provenance, variable coding, model assumptions, or reproducibility, consult the corresponding documentation and notebooks in this repository.

---

*Research transparency note: All numerical results described as preliminary must be re-generated and verified against the committed code before being presented as final findings.*
