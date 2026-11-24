# Marketing Campaign Statistical Analysis

Analysis of five anonymised marketing campaigns to assess CPA and conversion performance, test whether observed differences are statistically reliable, and develop a cautious, illustrative **$500,000 monthly budget allocation**.

## How to run
1. Open `lab_statistical_analysis_STUDENT.ipynb` in VS Code or Jupyter with a Python kernel.
2. Download the Criteo attribution dataset and place `criteo_attribution_dataset.tsv.gz` in the project root. The source archive is excluded from GitHub because of its size. The processed data is available in `outputs/marketing_data.csv`.
3. Install any missing Python dependencies used by the notebook (including `numpy`, `pandas`, `scipy`, `statsmodels`, `matplotlib`, and `seaborn`).
4. **Restart Kernel → Run All**. Check that the notebook completes without errors and regenerates the files in `outputs/`.

## Method and results
The notebook builds daily campaign metrics, visualises CPA and conversion-rate distributions, runs pairwise Welch t-tests with Cohen's d and Fisher's exact tests, applies Bonferroni and BH-FDR corrections, estimates simulated statistical power, and calculates bootstrap confidence intervals.

**Key results:** 9/10 CPA comparisons and 9/10 conversion-rate comparisons were significant; all 9 remained significant after both multiple-comparison corrections. Campaign `30801593` had the lowest observed mean daily CPA, while `10341182` had the highest conversion rate (23.64%). See `lab_proof.md` for the evidence and `outputs/executive_memo.md` for the decision rationale.


**Budget recommendation:** A provisional $500,000 monthly budget was allocated across five campaigns based on CPA rankings. Campaign `30801593` received the highest allocation (33.33%, approximately $166,667). All allocations fall within the required 5%–35% limits. ROAS was excluded because revenue data is unavailable.

## File map
| Path | Purpose |
|---|---|
| `lab_statistical_analysis_STUDENT.ipynb` | Complete reproducible analysis |
| `criteo_attribution_dataset.tsv.gz` | Source data archive |
| `instructions.md` | Lab instructions |
| `lab_proof.md` | Reviewer entry point: workflow, evidence, outputs, limitations |
| `outputs/marketing_data.csv` | Processed analysis data |
| `outputs/group_metrics_overview.png` | Campaign metrics overview |
| `outputs/group_distributions.png` | Daily metric distributions |
| `outputs/metric_comparison_heatmap.png` | Pairwise CPA p-values |
| `outputs/rate_comparison.png` | Campaign conversion rates |
| `outputs/correction_comparison.png` | Significance before and after corrections |
| `outputs/power_analysis_cpa.png` | Simulated CPA detection power |
| `outputs/executive_memo.md` | Findings, budget scenario and caveats |
| `reflection.md` | Optional learning reflection, if completed |

## Important limitations
Costs are anonymised and revenue is unavailable. The CPA ranking is therefore based on **anonymised cost units**, not verified dollars; ROAS and profit cannot be calculated. The $500,000 allocation is illustrative and must be tested against actual cost, revenue and campaign capacity before implementation. Power estimates rely on simulated assumptions.

For reviewer evidence and the main conclusions, start with **[`lab_proof.md`](lab_proof.md)**.
