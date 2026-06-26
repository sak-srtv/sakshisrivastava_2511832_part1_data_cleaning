# Cleaning Log New

Applied business rules to `cleaned_orders.xlsx` and recorded every decision in this log.

## Business rules applied

1. Missing `region` values were filled as `Unknown` and flagged in `cleaning_flags`.
2. Missing `ship_mode` values were filled as `Unknown` and flagged in `cleaning_flags`.
3. Missing `discount` values were treated as `0` only when `sales`, `cost`, `profit`, `unit_price`, and `quantity` were all present and valid.
4. Negative discount values were flagged invalid.
5. Discount values above the allowed range (> 1.0) were flagged invalid.
6. Cancelled orders were excluded from completed sales summary.
7. Failed payment orders were excluded from completed sales summary.
8. Refunded orders were marked for separate refund summary.
9. Ship dates before order dates were flagged as invalid shipping records.

## Summary of decisions

- Missing region filled: 26
- Missing ship_mode filled: 22
- Missing discount rows: 18
- Missing discount treated as 0: 18
- Missing discount not filled: 0
- Negative discount rows flagged: 16
- Discount above allowed range rows flagged: 0
- Cancelled orders excluded from completed sales summary: 146
- Failed payment orders excluded from completed sales summary: 69
- Refunded orders marked for separate summary: 72
- Ship date before order date flagged: 94

## Notes

- Every row has a `cleaning_flags` entry, multiple rules are concatenated with semicolons.
- `discount_cleaned` contains numeric discount values normalized from raw discount input.
- `include_in_completed_sales` is `False` for cancelled or failed-payment rows.
- `include_in_refund_summary` is `True` for refunded payment rows.
- `order_date_parsed` and `ship_date_parsed` were created for shipping validation.

## Output files

- Processed workbook: `cleaned_orders_business_rules_new.xlsx`
- Cleaning log: `cleaning_log_new.md`

## Additional handling details

- Percent-formatted discounts such as `70%` were normalized to `0.70` when parsing.
- If a discount value could not be parsed, it was flagged as invalid in `cleaning_flags`.
