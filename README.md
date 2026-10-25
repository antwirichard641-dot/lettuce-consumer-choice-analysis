# Consumer Choices for Hydroponic and Organic Lettuce: A Discrete-Choice Analysis

## Project Overview

This project examines consumer stated choices for lettuce based on production method, organic status, and price. It uses a discrete-choice modelling approach to investigate how these attributes are associated with consumer preferences and the decision to purchase or select no purchase.

## Research Objectives

- Examine consumer preferences for hydroponic lettuce.
- Estimate the association between organic production and consumer choice.
- Assess the relationship between price and the probability of selection.
- Compare lettuce alternatives with the no-purchase option.
- Present results through reproducible statistical analysis and visualisations.

## Repository Structure

```text
lettuce-consumer-choice-analysis/
├── README.md
├── datasets/
│   ├── README.md
│   └── lettuce_consumer_choice_clean.csv
├── results/
│   ├── README.md
│   ├── lettuce_choice_model_results.csv
│   ├── lettuce_choice_findings_summary.csv
│   └── lettuce_choice_research_limitations.csv
├── findings/
│   ├── README.md
│   └── lettuce_choice_research_conclusion.md
├── figures/
│   ├── README.md
│   └── lettuce_choice_odds_ratios.png
└── [Jupyter notebooks]
```

*The structure above describes the intended organisation; filenames and locations should match the files actually committed to the repository.*

## Dataset

The cleaned dataset contains 4,752 alternative-level observations from 1,584 choice sets involving 198 participants. Each choice set contains three alternatives, including a no-purchase option.

Variables include:

| Variable | Description |
|---|---|
| `ID` | Participant identifier |
| `cset` | Choice-set identifier |
| `Alternative` | Alternative identifier |
| `Choice` | Indicates the selected alternative |
| `Hydro` | Hydroponic attribute indicator |
| `Organic` | Organic attribute indicator |
| `Price` | Alternative price |

## Methods

The project uses conditional logistic regression to analyse choices within choice sets. The explanatory attributes include hydroponic production, organic status, and price. Model estimates are interpreted using coefficient estimates, statistical uncertainty, and odds ratios where appropriate.

## Main Findings

Previously obtained model estimates suggested that:

- **Organic status:** positively associated with selection.
- **Price:** negatively associated with selection.
- **Hydroponic production:** the estimated association was uncertain; its confidence interval included an odds ratio of 1.
- **Product versus no purchase:** the model indicated a higher likelihood of selecting a product alternative than the no-purchase option.

These findings should be treated as provisional until the analysis notebooks have been executed and the reported estimates independently reproduced.

## Limitations

- The dataset represents stated choices rather than verified real-world purchases.
- The results describe associations and should not be interpreted as proof of causation.
- Findings depend on the dataset, model specification, and assumptions.
- Generalisation beyond the sampled participants requires caution.

## Reproducibility

The repository is intended to document the data, analysis workflow, model outputs, figures, findings, and limitations. Before drawing final conclusions, run the notebooks in sequence and verify that their outputs agree with the committed results.

## Research Integrity

The project aims to maintain transparent documentation, reproducible analysis, and appropriate interpretation of statistical evidence. Dataset provenance, variable definitions, model specifications, and any data-processing decisions should be documented as the project develops.
