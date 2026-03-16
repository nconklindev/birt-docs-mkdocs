---
title: 'Creating Computed Columns'
description: How to create computed columns in BIRT Studio using the custom functions provided.
---

## What are Computed Columns?

Computed Columns in BIRT Studio are columns that are created using the custom functions provided in BIRT Studio.
The [functions](#birt-studio-functions) in BIRT Studio are somewhat similar to function calls in a modern programming
language such as Python or JavaScript, written as `functionName(arg1, arg2, ...)`. The function is written in a
dedicated text box within the Computed Column window.

## Creating a Computed Column

1. Right-click on a column header and select **Column > New Computed Column**. The **New Computed Column** window opens.
2. In the _Column Label_ field, enter a label for the column. This will be the name that appears in the column header.
3. From the _Category_ dropdown, select the function category you want to browse. This updates the functions available in the _Select Function_ area.
4. To enter a custom expression, select _Advanced..._ from any category. The _Enter Expression_ text area will appear.
5. Enter your expression in the _Enter Expression_ text area.
6. Click **Validate** to check if the expression is valid. A confirmation dialog will appear if valid, or an error if invalid.
7. Click **OK** to close the dialog, then click **OK** in the **New Computed Column** window to save. Click **Cancel** to discard without saving.

!!! info

    If you are creating a computed column that is only being used in another computed column, a good practice is to
    set the label in camelCase so that it is easy to identify it from other computed columns and serves as a reminder
    that it is not being displayed in the final report.

!!! warning

    Column labels cannot be changed once the computed column has been saved. Make sure you are happy with the label
    before saving.

## BIRT Studio Functions

The functions in BIRT Studio are separated into the following categories in the UI:

- [Comparison](#comparison)
- [Text](#text)
- [Math](#math)
- [Date & Time](#date--time)

### Comparison

#### `BETWEEN`

Tests if a value is between two specified values.

**Syntax**

```
BETWEEN(value, upperBound, lowerBound)
```

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `value` | string, number, or date | Yes | The value to test. |
| `upperBound` | number | Yes | The first value in the range. String and date values must be enclosed in double quotation marks. |
| `lowerBound` | number | Yes | The second value in the range. String and date values must be enclosed in double quotation marks. |

**Returns** — boolean: `true` if the value is between the upper and lower bounds, `false` otherwise.

---

#### `IF`

Returns one value if a condition evaluates to `true`, or another value if it evaluates to `false`.

**Syntax**

```
IF(condition, doIfTrue, doIfFalse)
```

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `condition` | string | Yes | The condition to test. |
| `doIfTrue` | number, date, datetime, time, string, or boolean | Yes | The value to return if the condition is `true`. |
| `doIfFalse` | number, date, datetime, time, string, or boolean | Yes | The value to return if the condition is `false`. |

**Returns** — The `doIfTrue` value if the condition is `true`, or the `doIfFalse` value if the condition is `false`.

---

#### `IN`

Tests if a value is equal to any value in a list.

**Syntax**

```
IN(value, check1, ..., checkN)
```

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `value` | string, number, date, or datetime | Yes | The value to test. |
| `check1, ..., checkN` | string, number, date, or datetime | Yes | One or more values to compare against. Add as many as needed. |

**Returns** — boolean: `true` if the value equals any of the check values.

---

#### `ISNULL`

Tests if a value in a specified data field is null.

**Syntax**

```
ISNULL(value)
```

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `value` | field | Yes | The data field to check for null values. |

**Returns** — boolean: `true` if the field value is null, `false` otherwise.

---

#### `LIKE`

Tests if a string matches a pattern. The match is case-sensitive. Supports `%` (any sequence of characters) and `_` (any single character) as wildcards. Does not support full regex.

**Syntax**

```
LIKE(str, pattern)
```

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `str` | string | Yes | The string to evaluate. |
| `pattern` | string | Yes | The pattern to match. Must be enclosed in double quotation marks. |

**Returns** — boolean: `true` if the string matches the pattern, `false` otherwise.

---

#### `MATCH`

Tests if a pattern exists within a string using ECMAScript (JavaScript) regex syntax, as defined in Standard ECMA-262, Section 15.10.

**Syntax**

```
MATCH(str, pattern)
```

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `str` | string | Yes | The string to evaluate. |
| `pattern` | string | Yes | The ECMAScript regex pattern to match. |

**Returns** — boolean: `true` if the string matches the pattern, `false` otherwise.

---

#### `NOT`

Negates a boolean expression.

**Syntax**

```
NOT(expression)
```

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `expression` | boolean | Yes | The boolean value or expression to negate. |

**Returns** — boolean: `true` if the expression is `false`, and `false` if the expression is `true`.

---

#### `NOTNULL`

Tests if a value in a specified data field is not null.

**Syntax**

```
NOTNULL(value)
```

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `value` | field | Yes | The data field to check. |

**Returns** — boolean: `true` if the field value is not null, `false` otherwise.

---

### Text

#### `FIND`

Finds the position of a substring within a string. The search is case-sensitive.

**Syntax**

```
FIND(strToFind, str, startPosition?)
```

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `strToFind` | string | Yes | The substring to search for. |
| `str` | string | Yes | The string to search within. |
| `startPosition` | number | No | The position in `str` where the search starts. |

**Returns** — number: The position of the substring within the string.

---

#### `LEFT`

Extracts a substring from the beginning of a string.

**Syntax**

```
LEFT(str, n?)
```

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `str` | string | Yes | The string from which to extract a substring. |
| `n` | number | No | The number of characters to extract from the left. If omitted, returns only the first character. If `0`, returns an empty string. If greater than the string length, returns the entire string. |

**Returns** — string: A substring of the specified length from the start of the string.

---

#### `LEN`

Counts the number of characters in a string.

**Syntax**

```
LEN(str)
```

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `str` | string | Yes | The string expression to evaluate. |

**Returns** — number: The number of characters in the string.

---

#### `LOWER`

Converts all letters in a string to lowercase.

**Syntax**

```
LOWER(str)
```

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `str` | string | Yes | The string to convert. |

**Returns** — string: The string converted to lowercase.

---

#### `RIGHT`

Extracts a substring from the end of a string.

**Syntax**

```
RIGHT(str, n?)
```

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `str` | string | Yes | The string from which to extract a substring. |
| `n` | number | No | The number of characters to extract from the right. If omitted, returns only the last character. |

**Returns** — string: A substring of the specified length from the end of the string.

---

#### `SEARCH`

Finds the position of a substring within a string. Supports wildcard characters. The first character in a string is position `1`. Returns `0` if the substring is not found.

**Syntax**

```
SEARCH(strToFind, str, startPosition?)
```

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `strToFind` | string | Yes | The substring to search for. |
| `str` | string | Yes | The string to search within. |
| `startPosition` | number | No | The position in `str` where the search starts. |

**Returns** — number: The position of the substring in the string, or `0` if not found.

---

#### `TRIM`

Removes leading and trailing spaces from a string. Does not remove spaces between words.

**Syntax**

```
TRIM(str)
```

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `str` | string | Yes | The string to trim. |

**Returns** — string: The string with leading and trailing spaces removed.

---

#### `TRIMLEFT`

Removes leading spaces from a string.

**Syntax**

```
TRIMLEFT(str)
```

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `str` | string | Yes | The string to trim. |

**Returns** — string: The string with leading spaces removed.

---

#### `TRIMRIGHT`

Removes trailing spaces from a string.

**Syntax**

```
TRIMRIGHT(str)
```

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `str` | string | Yes | The string to trim. |

**Returns** — string: The string with trailing spaces removed.

---

#### `UPPER`

Converts all letters in a string to uppercase.

**Syntax**

```
UPPER(str)
```

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `str` | string | Yes | The string to convert. |

**Returns** — string: The string converted to uppercase.

---

### Math

#### `ABS`

Returns the absolute value of a number, regardless of its sign.

**Syntax**

```
ABS(number)
```

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `number` | number | Yes | A numeric expression. |

**Returns** — number: The absolute value of the number.

---

#### `CEILING`

Returns the smallest integer greater than or equal to a number, rounded up to the nearest specified multiple.

**Syntax**

```
CEILING(number, significance)
```

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `number` | number | Yes | The numeric value to round up. |
| `significance` | number | Yes | The multiple to which to round. |

**Returns** — number: The smallest integer greater than or equal to the number.

---

#### `MOD`

Returns the remainder when one number is divided by another.

**Syntax**

```
MOD(number, divisor)
```

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `number` | number | Yes | The numeric value to divide. |
| `divisor` | number | Yes | The numeric value to divide by. |

**Returns** — number: The remainder of `number` divided by `divisor`.

---

#### `ROUND`

Rounds a number to a specified number of decimal places.

**Syntax**

```
ROUND(number, decimalPlaces?)
```

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `number` | number | Yes | The numeric value to round. |
| `decimalPlaces` | number | No | The number of decimal places to round to. |

**Returns** — number: The number rounded to the specified decimal places.

---

#### `ROUNDDOWN`

Rounds a number down (toward zero) to a specified number of decimal places.

**Syntax**

```
ROUNDDOWN(number, decimalPlaces?)
```

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `number` | number | Yes | The numeric value to round. |
| `decimalPlaces` | number | No | The number of decimal places to round to. Defaults to `0` if omitted. |

**Returns** — number: The number rounded down to the specified decimal places.

---

#### `ROUNDUP`

Rounds a number up (away from zero) to a specified number of decimal places.

**Syntax**

```
ROUNDUP(number, decimalPlaces?)
```

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `number` | number | Yes | The numeric value to round. |
| `decimalPlaces` | number | No | The number of decimal places to round to. Defaults to `0` if omitted. |

**Returns** — number: The number rounded up to the specified decimal places.

---

#### `SQRT`

Returns the square root of a number.

**Syntax**

```
SQRT(number)
```

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `number` | number | Yes | The numeric value to find the square root of. |

**Returns** — number: The square root of the specified number.

---

### Date & Time

#### `ADD_DAY`

Returns a date that is a specified number of days from a given date.

**Syntax**

```
ADD_DAY(date, daysToAdd)
```

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `date` | date | Yes | The start date. |
| `daysToAdd` | number | Yes | The number of days to add. Use a negative number to subtract. |

**Returns** — date: The resulting date.

---

#### `ADD_HOUR`

Returns a datetime that is a specified number of hours from a given date. If the start date has no time value, midnight (12:00 AM) is assumed.

**Syntax**

```
ADD_HOUR(date, hoursToAdd)
```

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `date` | date | Yes | The start date. If no time value is present, midnight is assumed. |
| `hoursToAdd` | number | Yes | The number of hours to add. Use a negative number to subtract. |

**Returns** — datetime: The resulting date and time.

---

#### `ADD_MINUTE`

Returns a datetime that is a specified number of minutes from a given date. If the start date has no time value, midnight (12:00 AM) is assumed.

**Syntax**

```
ADD_MINUTE(date, minutesToAdd)
```

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `date` | date | Yes | The start date. If no time value is present, midnight is assumed. |
| `minutesToAdd` | number | Yes | The number of minutes to add. Use a negative number to subtract. |

**Returns** — datetime: The resulting date and time.

---

#### `ADD_MONTH`

Returns a date that is a specified number of months from a given date.

**Syntax**

```
ADD_MONTH(date, monthsToAdd)
```

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `date` | date | Yes | The start date. |
| `monthsToAdd` | number | Yes | The number of months to add. Use a negative number to subtract. |

**Returns** — date: The resulting date.

---

#### `ADD_QUARTER`

Returns a date that is a specified number of quarters from a given date.

**Syntax**

```
ADD_QUARTER(date, quartersToAdd)
```

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `date` | date | Yes | The start date. |
| `quartersToAdd` | number | Yes | The number of quarters to add. Use a negative number to subtract. |

**Returns** — date: The resulting date.

---

#### `ADD_SECOND`

Returns a datetime that is a specified number of seconds from a given date.

**Syntax**

```
ADD_SECOND(date, secondsToAdd)
```

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `date` | date | Yes | The start date. |
| `secondsToAdd` | number | Yes | The number of seconds to add. Use a negative number to subtract. |

**Returns** — datetime: The resulting date and time.

---

#### `ADD_WEEK`

Returns a date that is a specified number of weeks from a given date.

**Syntax**

```
ADD_WEEK(date, weeksToAdd)
```

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `date` | date | Yes | The start date. |
| `weeksToAdd` | number | Yes | The number of weeks to add. Use a negative number to subtract. |

**Returns** — date: The resulting date.

---

#### `ADD_YEAR`

Returns a date that is a specified number of years from a given date.

**Syntax**

```
ADD_YEAR(date, yearsToAdd)
```

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `date` | date | Yes | The start date. |
| `yearsToAdd` | number | Yes | The number of years to add. Use a negative number to subtract. |

**Returns** — date: The resulting date.

---

#### `DAY`

Returns the day of the month for a specified date value.

**Syntax**

```
DAY(date)
```

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `date` | date | Yes | A date expression. |

**Returns** — number: A number from `1` to `31` representing the day of the month.

---

#### `DIFF_DAY`

Calculates the number of days between two date values.

**Syntax**

```
DIFF_DAY(date1, date2)
```

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `date1` | date | Yes | The first date value. |
| `date2` | date | Yes | The second date value. |

**Returns** — number: The number of days between the two dates.

---

#### `DIFF_HOUR`

Calculates the number of hours between two date values. If a date has no time value, midnight (12:00 AM) is assumed.

**Syntax**

```
DIFF_HOUR(date1, date2)
```

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `date1` | date | Yes | The first date value. If no time value is present, midnight is assumed. |
| `date2` | date | Yes | The second date value. If no time value is present, midnight is assumed. |

**Returns** — number: The number of hours between the two dates.

---

#### `DIFF_MINUTE`

Calculates the number of minutes between two date values. If a date has no time value, midnight (12:00 AM) is assumed.

**Syntax**

```
DIFF_MINUTE(date1, date2)
```

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `date1` | date | Yes | The first date value. If no time value is present, midnight is assumed. |
| `date2` | date | Yes | The second date value. If no time value is present, midnight is assumed. |

**Returns** — number: The number of minutes between the two dates.

---

#### `DIFF_MONTH`

Calculates the number of months between two date values. The result is calculated by subtracting the month number of `date1` from the month number of `date2`.

**Syntax**

```
DIFF_MONTH(date1, date2)
```

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `date1` | date | Yes | The first date value. |
| `date2` | date | Yes | The second date value. |

**Returns** — number: The number of months between the two dates.

---

#### `DIFF_QUARTER`

Calculates the number of quarters between two date values.

**Syntax**

```
DIFF_QUARTER(date1, date2)
```

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `date1` | date | Yes | The first date value. |
| `date2` | date | Yes | The second date value. |

**Returns** — number: The number of quarters between `date1` and `date2`.

---

#### `DIFF_SECOND`

Calculates the number of seconds between two date values.

**Syntax**

```
DIFF_SECOND(date1, date2)
```

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `date1` | date | Yes | The first date value. |
| `date2` | date | Yes | The second date value. |

**Returns** — number: The number of seconds between `date1` and `date2`.

---

#### `DIFF_WEEK`

Calculates the number of weeks between two date values.

**Syntax**

```
DIFF_WEEK(date1, date2)
```

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `date1` | date | Yes | The first date value. |
| `date2` | date | Yes | The second date value. |

**Returns** — number: The number of weeks between `date1` and `date2`.

---

#### `DIFF_YEAR`

Calculates the number of years between two date values.

**Syntax**

```
DIFF_YEAR(date1, date2)
```

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `date1` | date | Yes | The first date value. |
| `date2` | date | Yes | The second date value. |

**Returns** — number: The number of years between `date1` and `date2`.

---

#### `MONTH`

Returns the month for a specified date value.

**Syntax**

```
MONTH(date, option?)
```

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `date` | date | Yes | The date value from which to extract the month. |
| `option` | number | No | The format of the returned value. Defaults to `1` if omitted. |

**Option values:**

| Value | Returns |
|-------|---------|
| `1` | Month as a number from `1` to `12` |
| `2` | Full month name (locale-specific) |
| `3` | Abbreviated month name (locale-specific) |

**Returns** — number or string: The month of the specified date.

---

#### `NOW`

Returns the current date and time.

**Syntax**

```
NOW()
```

This function takes no parameters.

**Returns** — datetime: The current date and time.

---

#### `QUARTER`

Returns the quarter number for a specified date value.

**Syntax**

```
QUARTER(date)
```

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `date` | date | Yes | The date value from which to extract the quarter. |

**Returns** — number: A number from `1` to `4` representing the quarter.

---

#### `TODAY`

Returns the current date with a time value of midnight (12:00 AM).

**Syntax**

```
TODAY()
```

This function takes no parameters.

**Returns** — date: The current date in the format `MMM dd, yyyy 12:00 AM`.

---

#### `WEEK`

Returns the week of the year for a specified date value.

**Syntax**

```
WEEK(date)
```

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `date` | date | Yes | The date value from which to extract the week of the year. |

**Returns** — number: A number from `1` to `52` representing the week of the year.

---

#### `WEEKDAY`

Returns the day of the week for a specified date value.

**Syntax**

```
WEEKDAY(date, option?)
```

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `date` | date | Yes | The date value from which to extract the day of the week. |
| `option` | number | No | The format of the returned value. Defaults to `1` if omitted. |

**Option values:**

| Value | Returns |
|-------|---------|
| `1` | Day as a number: `1` (Sunday) to `7` (Saturday) |
| `2` | Day as a number: `1` (Monday) to `7` (Sunday) |
| `3` | Day as a number: `0` (Monday) to `6` (Sunday) |
| `4` | Full weekday name (locale-specific) |
| `5` | Abbreviated weekday name (locale-specific) |

**Returns** — number or string: The day of the week for the specified date.

---

#### `YEAR`

Returns the four-digit year for a specified date value.

**Syntax**

```
YEAR(date)
```

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `date` | date | Yes | The date value from which to extract the year. |

**Returns** — number: The four-digit year for the specified date.
