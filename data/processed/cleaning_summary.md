# Cleaning Summary

## Dataset shapes
- Before cleaning: (4410, 29)
- After cleaning: (4410, 27)

## Columns dropped
- employee_count, over_18, standard_hours

## Missing values
- Missing values were found in:
  - work_life_balance
  - environment_satisfaction
  - job_satisfaction
  - num_companies_worked
  - total_working_years
- All missing percentages were low, so median imputation was applied to numeric columns.

## Duplicate check
- Fully duplicated rows: 0
- Duplicated employee IDs: 0
- No duplicate rows were removed because no true duplicates were found.

## Data type review
- Numeric variables already had appropriate numeric types.
- Categorical variables were stored as object/text.
- The raw attendance files contained date/time records, which were used to engineer avg_working_hours.
- The original date/time columns were not directly merged into the final employee-level dataset.

## Attendance feature engineering
- avg_working_hours was created from in_time.csv and out_time.csv.
- Daily working hours were calculated as out_time minus in_time.
- Only valid working-hour records between 0 and 16 hours were used.
- The final feature was aggregated at employee level and merged into df_clean.

## Categorical values
- No major categorical inconsistencies were found.
- Basic string cleaning was applied.

## Clustering note
- The following columns will be excluded from clustering input later:
  - employee_id, employee_count, over_18, standard_hours
