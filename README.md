# New Onboarding And Activation Campaign. KPI Experiment Analysis

**Student Name:** Ansh Singh

**Student ID:** 2511922

**Repository:** anshsingh_2511922_part2_kpi_experiment

---

## 1. Business Context

This company sells a subscription product. They made an onboarding campaign and wanted to test if it works better than the old one. The company split users into two groups:

- **Control Group** – these users got the onboarding experience with 693 users

- **Treatment Group** – these users got the new campaign experience with 715 users

The main question is – should the company switch everyone to the new campaign or not?

**Business Problem:**

The company wants to know if the new campaign is actually helping more users convert to paid subscribers. This matters because paid users means more revenue.. The company also needs to make sure the new campaign is not causing other problems like too many refund requests or support complaints. The company needs data-backed evidence before making this decision.

---

## 2. Dataset Description

**File:** `data/campaign_experiment_data.xlsx`

**Total Records:** 1408 records after removing 8 duplicates, which left 1400 records

The dataset has 16 columns:

| Column | What it means |

|---|---|

user_id | Unique ID for each user |

| signup_date | When the user signed up |

| experiment_group | Control or Treatment |

| region | Which region the user is from |

device_type | Mobile, Desktop or Tablet |

| traffic_source | How they found the product |

| plan_type Free, Basic or Premium |

| visited_landing_page | Did they visit the landing page?

| started_trial | Did they start a trial?

| completed_onboarding | Did they finish onboarding?

| converted_to_paid | Did they become a paying user?

| revenue_30d | How revenue they generated in 30 days |

| support_tickets_30d | Number of support tickets raised |

| refund_requested | Did they ask for a refund?

| days_to_convert | How days it took to convert

| engagement_score | A score showing how engaged the user was

---

## 3. North Star Metric

**I chose: Paid Conversion Rate**

This means – out of all users how many became paying customers.

**Why I chose this:**

I think paid conversion rate is the important metric here because the whole point of the campaign is to get more people to pay. Things like landing page visits and trial starts are good. They do not directly bring in money. When a user actually pays does the business benefit.

Other metrics like engagement score or days to convert are useful to understand user behavior. They are supporting metrics, not the main success measure.

**What could go wrong:**

If the company only focuses on conversion rate and ignores everything they might end up getting a lot of users who convert but then ask for refunds or raise too many support tickets. That would actually hurt the company even if conversion looks good on paper.

---

## 4. KPI Tree Summary

I made a KPI tree to show how the North Star metric is connected to metrics.

The tree has 3 driver areas:

**Driver 1 – Activation Funnel**

This tracks how users move through the steps before converting.

**Driver 2 – Revenue Quality**

This looks at how much money's actually being generated.

**Driver 3 – Engagement And Retention**

This includes engagement score, segment-level conversion rates and which regions/devices/traffic sources are performing best.

**Guardrail Metrics I tracked:**

- Refund Rate

- Support Ticket Rate

- Revenue per Converted User

- Social Traffic Conversion Rate

---

## 5. Experiment Analysis Approach

**File:** `analysis/experiment_analysis.xlsx`

Before doing the analysis I cleaned the data.

| Issue Found | Details | What I Did |

|---|---|---|

| Duplicate user IDs | 8 duplicates found | Removed them kept record |

| Missing device_type | 18 values missing | Filled with 'Unknown' |

| Missing traffic_source | 24 values missing | Filled with 'Unknown' |

| Missing engagement_score | 14 values missing | Replaced with average of that group |

| Missing days_to_convert | 1336 missing | This is normal – converted users have this value |

| Revenue outliers | Some high values found | Flagged them but kept in dataset |

| Binary column check | checked all 0/1 columns | No invalid values found |

| Group balance | 693 vs 715 users | Roughly balanced no issue |

After cleaning I calculated all the required metrics and also did segment analysis by region, device type, traffic source and plan type.

---

## 6. Hypothesis Test Summary

**File:** `analysis/hypothesis_test_notes.md`

I used a Two-Proportion Z-Test to check if the improvement in conversion rate is real or just happened by chance.

- **H0 (Null):** Treatment conversion rate is same or lower than Control

- **H1 (Alternate):** Treatment conversion rate is higher than Control

- **Test type:** One-tailed

- **Alpha level:** 0.05

**Results:**

- Control conversion rate: 3.17%

- Treatment conversion rate: 6.99%

- Z-statistic: 3.2519

- P-value: 0.000573

Since p-value is less than 0.05 I rejected the null hypothesis. This means the improvement is statistically significant and not random chance.

---

## 7. Guardrail Metrics

Even though conversion rate improved a lot I noticed some warning signs:

| Guardrail | Control | Treatment | My Concern |

|---|---|---|---|

| Refund Rate | 0.00% | 0.42% Treatment introduced refunds which did not exist before |

| Support Ticket Rate | 14.72% | 24.76% | Big jump – new campaign might be confusing users |

| Revenue per Converted User | $1,630 | $770 | Treatment users are paying less on average |

| Social Traffic Conversion | 7.69% 6.02% | Campaign actually performs worse for social users |

These guardrail issues are important. Just because conversion doubled does not mean the campaign is perfect.

---

## 8. Final Recommendation

**My recommendation: Launch for some segments, not everyone **

The conversion improvement is real and statistically proven.. The guardrail concerns mean the company should be careful.

I would suggest:

- Launch the campaign for mobile users, referral traffic and North/South/East regions where it clearly works well

- Do not launch yet for social traffic and West region – needs more work

- Keep monitoring refund rate and support ticket rate after launch

- Investigate why revenue per converted user dropped so much

Full details are in `outputs/recommendation_memo.md`.

---

## 9. Assumptions and Limitations

- I removed 8 duplicate records. Kept the first occurrence

- Missing values were handled as described above

- I assumed that days_to_convert being blank = user did not convert

- The data only covers Jan–May 2025 so long term effects are not known

- Some outlier revenue values were flagged but kept

---

## 10. Screenshots

| File | What it shows |

|---|---|

screenshots/summary_metrics.png` | Bar charts comparing Control vs Treatment on key metrics |

| `screenshots/hypothesis_test_output.png` | The Z-test inputs and outputs, with the decision |

| `screenshots/kpi_tree_preview.png` | Preview of the KPI tree I made |

---

## 11. Folder Structure

```

part2_kpi_experiment/

├── data/

│   └── campaign_experiment_data.xlsx

├── analysis/

│   ├── experiment_analysis.xlsx

│   └── hypothesis_test_notes.md

├── outputs/

│   ├── kpi_tree.png

│   ├── experiment_summary.xlsx

│   └── recommendation_memo.md

├── screenshots/

│   ├── summary_metrics.png

│   ├── hypothesis_test_output.png

│   └── kpi_tree_preview.png

└── README.md

```
