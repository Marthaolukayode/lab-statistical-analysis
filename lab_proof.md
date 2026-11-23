# Lab Proof — Statistical Analysis of Marketing Campaigns

## Reviewer entry point
Run `lab_statistical_analysis_STUDENT.ipynb` from top to bottom. The notebook loads the source data, constructs daily campaign metrics, performs statistical tests and simulations, and writes the figures and memo to `outputs/`.

## Input and workflow
- **Input:** `criteo_attribution_dataset.tsv.gz` (source archive); processed analysis data: `outputs/marketing_data.csv`.
- **Groups:** Five anonymised campaign IDs; 31 daily observations for four campaigns and 30 for one (155 daily observations total).
- **Metrics:** CPA, click-through rate and conversion rate; campaign totals and daily distributions.
- **Tests:** Pairwise Welch t-tests and Cohen's d for daily CPA and conversion rate; Fisher's exact tests for converted/non-converted clicks; Bonferroni and Benjamini–Hochberg (BH-FDR) corrections; simulated power and bootstrap 95% confidence intervals.
- **Decision output:** Provisional CPA-based allocation of $500,000, capped at 35% per campaign. See `outputs/executive_memo.md`.

## Evidence and findings
- **Pairwise CPA:** 9 of 10 comparisons significant before and after both corrections.
- **Conversion rates:** 9 of 10 comparisons significant with Welch's t-test and Fisher's exact test; zero disagreements between the tests.
- **Non-significant CPA pair:** Campaigns `5061834` and `17686799` (p ≈ 0.7597).
- **Non-significant conversion pair:** Campaigns `5061834` and `30801593` (Fisher p ≈ 0.3109).
- **Highest observed conversion rate:** `10341182` (23.64%); **lowest:** `17686799` (5.17%).
- **Lowest observed mean daily CPA:** `30801593` (~0.0012 in anonymised cost units).
- **Power simulation:** Under the notebook's assumed 15% daily CPA standard deviation, 31 days are sufficient for simulated 15–20% differences at 80% power, but not for 5–10% differences. This simulation is assumption-dependent.

## Illustrative budget allocation
| Campaign | Allocation | USD |
|---|---:|---:|
| 30801593 | 33.33% | $166,666.67 |
| 10341182 | 26.67% | $133,333.33 |
| 15398570 | 20.00% | $100,000.00 |
| 5061834 | 13.33% | $66,666.67 |
| 17686799 | 6.67% | $33,333.33 |
| **Total** | **100%** | **$500,000.00** |

## Final outputs
- `outputs/marketing_data.csv`
- `outputs/group_metrics_overview.png`
- `outputs/group_distributions.png`
- `outputs/metric_comparison_heatmap.png`
- `outputs/rate_comparison.png`
- `outputs/correction_comparison.png`
- `outputs/power_analysis_cpa.png`
- `outputs/executive_memo.md`

## Limitation encountered
The dataset uses anonymised costs and lacks revenue. Therefore, CPA cannot be interpreted as a verified dollar cost, and ROAS, profit and financial scalability cannot be established. The proposed budget is a **scenario for further testing**, not a validated investment decision. Results may also depend on attribution assumptions and dependence among observations.

## Reproduction check
Before submission, run **Restart Kernel → Run All** in VS Code/Jupyter, verify there are no errors, and confirm all listed output files were regenerated. Remove any original instructor TODO code cells superseded by the completed cells.
