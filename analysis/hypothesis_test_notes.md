# Hypothesis Test Notes

---

## What I am testing

I want to check if the new campaign, which is the Treatment group actually improved the paid conversion rate compared to the experience, which is the Control group. I want to know if the difference we see is real or just by luck.

The paid conversion rate is what I am looking at. This tells us what percentage of users converted to a paid plan. I chose the paid conversion rate because it is very important to our business and it helps us make decisions. If this metric improves significantly it means the campaign is actually working.

---

## Metric I chose for testing

The metric I chose for testing is the **Paid Conversion Rate**. This metric is important because it shows us what percentage of users converted to a paid plan.

I chose the paid conversion rate because it is our metric and it is directly connected to the business decision. If the paid conversion rate improves it means the campaign is working.

---

## My Hypotheses

My **Null Hypothesis** is that the paid conversion rate in the Treatment group is less than or equal to the paid conversion rate in the Control group. This means the new campaign did not actually help.

My **Alternate Hypothesis** is that the paid conversion rate in the Treatment group is greater than the paid conversion rate in the Control group. This means the new campaign did improve conversion.

---

## Test Setup

| Parameter | Value |

|---|---|

Test Type | Two-Proportion Z-Test |

| Test Direction | One-tailed, because we only care if the Treatment group is better |

| Significance Level | 0.05 |

| Critical Z-value | 1.6449 |

I used the Z-test because we are comparing two proportions, which're percentages, from two large independent groups. Both groups have than 30 samples so the normal approximation works fine here.

I used a one-tailed test because we are only asking if the Treatment group is better not if it's different. One-tailed tests are used when we have a direction in mind which is the case with the Treatment group.

---

## Test Inputs

| Input | Control group | Treatment group |

|---|---|---|

| Total users 693 | 715 |

| Users who converted | 22 50 |

| Conversion rate | 3.17% | 6.99% |

| Pooled proportion | 0.0514 |. |

| Standard error | 0.0103 |. |

---

## Test Output

| Result | Value |

|---|---|

| Z-Statistic | 3.2519 |

P-Value | 0.000573 |

Critical Z-value | 1.6449 |

| Decision | Reject the Null Hypothesis |

The decision rule I used is: if the Z-Statistic is greater than 1.6449 and the P-Value is less than 0.05 then we reject the Null Hypothesis. The Z-Statistic is 3.2519, which's greater than 1.6449 and the P-Value is 0.000573, which is less than 0.05. So I reject the Null Hypothesis.

---

## What this means

The result is statistically significant. The Treatment group conversion rate of 6.99% is significantly higher than the Control group conversion rate of 3.17%. The relative improvement is +120%.

The P-Value of 0.000573 means there is a 0.057% chance of seeing this result if the Null Hypothesis was true. That is very small. I am confident the campaign made a real difference.

---

## But wait – there are some problems too

Even though the conversion rate improved a lot I noticed some other metrics got worse. The Treatment group had some issues.

1. **Support Ticket Rate** went up from 14.72% to 24.76%. This is a jump and means the new campaign might be creating confusion for users. More support tickets mean cost for the company.

2. **Revenue, per converted user** dropped from $1,630 to $770. This is concerning because even though more people converted they are paying less. The total revenue impact might not be as good as it looks.

3. **Refund rate** increased from 0% to 0.42%. This is small. It was zero before so something changed.

4. **Social traffic conversion** actually went down. The Treatment group performed worse for media users going from 7.69% to 6.02%.

So my conclusion is: the campaign works, but it should not be launched for everyone immediately. A partial launch makes sense until these issues are understood better.

---

*Analysis done on 1400 records after removing 8 duplicate user IDs from the dataset.*
