# AtliQ — HR Attendance & Workforce Intelligence: Analysis Report

**Period analysed:** 1 Apr 2022 – 17 Jun 2022 (the date filter applied on the dashboard)
**Source:** `datasets/Attendance-Sheet-2022-2023.xlsx` (tabs: Apr 2022, May 2022, June 2022, Attendance Key)
**Dashboard:** `dashboard/AtliQ — HR Attendance & Workforce Intelligence Project.pbix`
**Business problem:** `business-problem/problem.pdf`

## 1. Business Problem Recap

AtliQ tracks attendance in manual monthly Excel sheets (one tab per month, one row per employee, one column per day, with coded statuses such as P, WFH, PL, SL, LWP and WO). The data covers April–June 2022 and about **74 distinct employees**. The sheets record what happened but are hard to read as a whole, so HR has no quick view of attendance and work-from-home patterns. This project answers five questions: how present the workforce is, whether attendance is improving or dipping, whether there is a weekday pattern, which employees are outliers, and whether leave usage is healthy.

## 2. Executive Summary

Across about 2,386 working-day records for **74 employees**, the workforce was **present on-site 91.8%** of working days, **worked from home 10.0%**, and took **sick leave on only 1.1%**. Attendance was weakest in May and on Fridays, when WFH and sick leave rise together. 

## 3. Data & Method

| Step | What was done |
|---|---|
| Consolidate | Three monthly tabs (wide format, one column per date) were unpivoted into one long table: Employee Code, Name, Date, Value |
| Exclude | Weekly Off (`WO`) records are removed, matching the report-level filter in the dashboard, so they do not dilute the rates |
| Scope | Dates up to 17 Jun 2022, matching the dashboard's page filter. Entries after about 19 Jun are sparse |
| KPIs | `Presence % = DIVIDE([Present Days], [Total Working Days], 0)`, `WFH % = DIVIDE([WFH Count], [Present Days], 0)`, `SL % = DIVIDE([SL Count], [Total Working Days], 0)`, `Total Employee Count = DISTINCTCOUNT('Attendance Final Data'[Employee Code])` |


## 4. Headline KPIs

| KPI | Value |
|---|---|
| Total employees (distinct employee codes) | **74** |
| Presence % | **91.8%** |
| WFH % | **10.0%** |
| Sick Leave % | **1.1%** |

## 5. Key Findings

| Month | Presence % | WFH % | SL % |
|---|---|---|---|
| Apr 2022 | 94.1% | 9.1% | 0.4% |
| May 2022 | 89.7% | 11.2% | 1.7% |
| Jun 2022 (1–17) | 91.8% | 9.4% | 1.% | 

## 6. Recommendations

1. **Set a clear expectation for Thursday and Friday.** Consider anchor days or a team-level rota so that office presence does not drop below about 80%.
2. **Review the May dip.** Check whether it was driven by festivals, deadlines or illness, and plan staffing for the same period next year.
3. **Classify fully remote roles.** Tag the always-WFH employees as remote in the data so they stop distorting on-site presence KPIs.
4. **Monitor unpaid leave.** Track LWP % monthly and look at leave balances for employees who take it repeatedly.
5. **Follow up with the low-presence group.** Hold supportive conversations with the 14 employee records below 70% presence, using the employee table in the dashboard to filter them.
6. **Fix the data at the source.** Use unique employee IDs and standardise the sheet template.

## 7. Data Quality Notes

- **74 distinct employee codes** appear in the data, but 24 of them are shared by two or three different names, giving 99 distinct names. The headline employee count uses codes (74); person-level analysis uses names. Unique employee IDs are recommended.
- The file name says 2022–2023, but it contains only **April–June 2022**.
- Late-June rows are mostly blank, which is why June is scoped to 1–17 June.
- May starts on 2 May, so 1 May is missing from the data.

## 8. Dashboard Guide

| Area | Content |
|---|---|
| Title banner | AtliQ — HR Attendance & Workforce Intelligence Project |
| KPI cards | Total Employee Count, WFH %, Presence %, SL % |
| Slicers | Day of Week and Month |
| Trend charts | Presence % area chart, WFH % area chart, SL % area chart (by date) |
| Day-of-week tables | Presence %, WFH %, SL % by weekday |
| Employee table | Presence %, SL % and WFH % per employee |
| Daily detail matrix | Status by employee and date |
| Report filter | Excludes Weekly Off (WO) records |

## 9. Business Questions — Answered

| Business question | Answer from the data | Dashboard element |
|---|---|---|
| How present is the workforce overall? | 98.8% present, 10.0% WFH | Presence % card + trend area chart |
| How much WFH, and when? | 10.0% overall; peaks on Fridays (13.0%) overall and in May 15.9% | WFH % card + trend + weekday table |
| Is sick leave abnormal? | No, 1.1% overall; highest in May (1.7%) | SL % card + trend + weekday table |
| What happened on a given day? | Weakest week 2–8 May (78.4% presence) | Daily detail matrix + month / weekday slicers |

## 10. Success Criteria Check

- **Headline KPIs at a glance, filterable by month, weekday and employee:** met by the KPI cards and slicers.
- **Same KPI definitions every month:** met, since all measures use the same working-day denominator with weekly offs excluded.
- **Risks identifiable without opening raw sheets:** met through the weekday, trend and employee views.

## 11. Next Steps
- Add the remaining months, then year-on-year comparisons.
- Add department and location fields for team-level analysis.
- Add a rolling 4-week presence trend and alert thresholds.
