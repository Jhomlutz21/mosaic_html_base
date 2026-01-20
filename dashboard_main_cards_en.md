# Dashboard Main - card content (current view)

## Objective
Capture the visible information in each card of `dashboard_main.html` without changing it.

## Scope
- Literal content from the view.
- No assumptions about periods, comparisons, or data sources.
- Only blocks with charts (canvas).

## Visual order (per HTML)
1. Monthly performance (Profit & Loss) - `fintech-card-01`
2. Active licenses - `fintech-card-07`
3. Course progress - `fintech-card-08`
4. Balance distribution - `fintech-card-09`
5. Broker accounts - linked - `fintech-card-10`
6. Expert Advisors - active - `fintech-card-11`
7. Licenses - active - `fintech-card-12`
8. Courses - in progress - `fintech-card-13`
9. Account summary (table) - `fintech-card-14-a` to `fintech-card-14-e`

## Cards (details)

### 1) Monthly performance (Profit & Loss)
HTML name (comment): <!-- Line chart (Portfolio Returns) -->
Visible title: Monthly performance (Profit & Loss)
Type: Line chart
Canvas id: fintech-card-01
Legend id: fintech-card-01-legend
Current content / UI copy:
- Main value: "$1,284.60"
- Supporting text: "USD 62.4 daily average"
- Legend: container `fintech-card-01-legend` (empty list in HTML)
Metrics / Formula: N/A (literal content)
Sources: N/A
Rules / Notes: N/A
CTA: none
Empty state: none

### 2) Active licenses
HTML name (comment): <!-- Line chart (Portfolio Returns) -->
Visible title: Active licenses
Type: Line chart
Canvas id: fintech-card-07
Legend id: none
Current content / UI copy:
- Text: "Current license usage:"
- Value: "2 of 3"
- Percentage: "67%"
- Note: "Next renewal: 12/03/2026"
Metrics / Formula: N/A (literal content)
Sources: N/A
Rules / Notes: N/A
CTA: none
Empty state: none

### 3) Course progress
HTML name (comment): <!-- Line chart (Growth Portfolio) -->
Visible title: Course progress
Type: Line chart
Canvas id: fintech-card-08
Legend id: none
Current content / UI copy:
- Text: "Your course in progress:"
- Value: "64% completed"
- Note: "Course: Risk Management"
Metrics / Formula: N/A (literal content)
Sources: N/A
Rules / Notes: N/A
CTA: none
Empty state: none

### 4) Balance distribution
HTML name (comment): <!-- Pie chart (Portfolio Value) -->
Visible title: Balance distribution
Type: Pie chart
Canvas id: fintech-card-09
Legend id: fintech-card-09-legend
Current content / UI copy:
- Text: "Combined account balance:"
- Value: "$12,480.75"
- Legend: container `fintech-card-09-legend` (empty list in HTML)
Metrics / Formula: N/A (literal content)
Sources: N/A
Rules / Notes: N/A
CTA: none
Empty state: none

### 5) Broker accounts - linked
HTML name (comment): <!-- Line charts (Stock graphs) -->
Visible title: Broker accounts - linked
Type: Line chart (mini)
Canvas id: fintech-card-10
Legend id: none
Current content / UI copy:
- Value: "2"
- Change: "+1 (50%) - Today"
Metrics / Formula: N/A (literal content)
Sources: N/A
Rules / Notes: N/A
CTA: none
Empty state: none

### 6) Expert Advisors - active
HTML name (comment): <!-- Line charts (Stock graphs) -->
Visible title: Expert Advisors - active
Type: Line chart (mini)
Canvas id: fintech-card-11
Legend id: none
Current content / UI copy:
- Value: "4"
- Change: "+1 (33%) - Today"
Metrics / Formula: N/A (literal content)
Sources: N/A
Rules / Notes: N/A
CTA: none
Empty state: none

### 7) Licenses - active
HTML name (comment): <!-- Line charts (Stock graphs) -->
Visible title: Licenses - active
Type: Line chart (mini)
Canvas id: fintech-card-12
Legend id: none
Current content / UI copy:
- Value: "3"
- Change: "+0 (0%) - Today"
Metrics / Formula: N/A (literal content)
Sources: N/A
Rules / Notes: N/A
CTA: none
Empty state: none

### 8) Courses - in progress
HTML name (comment): <!-- Line charts (Stock graphs) -->
Visible title: Courses - in progress
Type: Line chart (mini)
Canvas id: fintech-card-13
Legend id: none
Current content / UI copy:
- Value: "2"
- Change: "+1 (100%) - Today"
Metrics / Formula: N/A (literal content)
Sources: N/A
Rules / Notes: N/A
CTA: none
Empty state: none

### 9) Account summary (table)
HTML name (comment): <!-- Table (Market Trends) -->
Visible title: Account summary
Type: Table
Canvas id: fintech-card-14-a, fintech-card-14-b, fintech-card-14-c, fintech-card-14-d, fintech-card-14-e
Legend id: none
Current content / UI copy:
- Columns: Area, Total, Trend, USD, Status
- Rows:
  - Area: "Sniper Advanced Panel" (Active), Total "3", Trend `fintech-card-14-a`, USD "$59.00", Status "Active"
  - Area: "PANDORA BOX EA" (Active), Total "2", Trend `fintech-card-14-b`, USD "$0.00", Status "Active"
  - Area: "Courses" (In progress), Total "2", Trend `fintech-card-14-c`, USD "$149.00", Status "In progress"
  - Area: "Expert Advisor" (Active), Total "1", Trend `fintech-card-14-d`, USD "$29.00", Status "Active"
  - Area: "Subscription" (Pro plan), Total "1", Trend `fintech-card-14-e`, USD "$59.00", Status "Renews 12/03"
Metrics / Formula: N/A (literal content)
Sources: N/A
Rules / Notes: N/A
CTA: none
Empty state: none
