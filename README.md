# Data-analyst-portfolio
SQL + Tableau project to analyze AWS cloud costs and provide dashboards for visibility and optimization.

## SUMMARY
Using SQL and Tableau, I analyzed AWS cost and usage data to identify the main cost drivers and spending trends. I create a dashboard that breaks down expenses by service, account, and usage type, providing visibility into cloud spending distribution and opportunities for cost optimization. 

## METHODOLOGY
To explore AWS cost and usage data, I used SQL for my own analysis before building visualizations in Tableau. The main steps included:
1. Monthly Spend Analysis - Querying total monthly costs top identify which month had the highest spending.
2. Service-Level-Analysis - Aggregating costs by service to determine which service contributed the most to cloud expenses.
3. Usage-Type Analysis - Breaking down costs by usage type to highlight where resources were driving the largest spend.

###MONTHLY SPEND ANALYSIS

```sql
SELECT TO_CHAR("Date", 'YYYY-MM') AS month,
SUM("Cost") AS total_spend
FROM aws_cloud_sample_data
GROUP BY TO_CHAR("Date", 'YYYY-MM')
ORDER BY month;
```
Result:
| month   | total_spend |
|---------|-------------|
| 2024-01 | 24740.94    |
| 2024-02 | 22585.57    |
| 2024-03 | 27410.64    |


###SERVICE-LEVEL-ANALYSIS

```sql
SELECT "Service",
SUM("Cost") AS total_spend
FROM aws_cloud_sample_data
GROUP BY "Service"
ORDER BY total_spend DESC;
```
Result:
| service  | total_spend   |
|----------|---------------|
| Lambda   | 15985.22      |
| EC2      | 15831.00      |
| DynamoDB | 14999.48      |
| S3       | 14767.38      |
| RDS      | 13154.07      |

###USAGE-TYPE ANALYSIS

```sql
SELECT "UsageType",
SUM("Cost") AS total_spend
FROM aws_cloud_sample_data
GROUP BY "UsageType"
ORDER BY total_spend DESC;
```
Result:
| service  | total_spend   |
|----------|---------------|
| Lambda   | 15985.22      |
| EC2      | 15831.00      |
| DynamoDB | 14999.48      |
| S3       | 14767.38      |
| RDS      | 13154.07      |

###TABLEAU DASHBOARD
After completing the SQL analysis. I built an interactive Tableau dashboard to visualize AWS cloud spending.
