# datagrip-data-extractors

## Description

This repository contains a collection of data extractors for [JetBrains DataGrip](https://www.jetbrains.com/datagrip/).

## Extractors

All extractors are located in the [extractors](extractors/) directory.

### 1. Pretty-Padded

This extractor script is based on the bundled "Pretty" extractor script. It adds padding to the output to make it easier to read.

#### Example

```sql
SELECT
    *
FROM (
         VALUES (1, 'one', CURRENT_TIMESTAMP, TRUE, 'a'),
                (2, 'two', CURRENT_TIMESTAMP, FALSE, 'b'),
                (3, 'three', CURRENT_TIMESTAMP, TRUE, 'c')
     ) AS t (num, txt, ts, bool,long_column_name_with_tiny_value);
```

With *built in* "Pretty" extractor:

```text
+---+-----+---------------------------------+-----+--------------------------------+
|num|txt  |ts                               |bool |long_column_name_with_tiny_value|
+---+-----+---------------------------------+-----+--------------------------------+
|1  |one  |2023-06-20 16:55:04.401217 +00:00|true |a                               |
|2  |two  |2023-06-20 16:55:04.401217 +00:00|false|b                               |
|3  |three|2023-06-20 16:55:04.401217 +00:00|true |c                               |
+---+-----+---------------------------------+-----+--------------------------------+
```

With *this custom* "Pretty-Padded" extractor:

```text
+-----+-------+-----------------------------------+-------+----------------------------------+
| num | txt   | ts                                | bool  | long_column_name_with_tiny_value |
+-----+-------+-----------------------------------+-------+----------------------------------+
| 1   | one   | 2023-06-20 16:55:04.401217 +00:00 | true  | a                                |
| 2   | two   | 2023-06-20 16:55:04.401217 +00:00 | false | b                                |
| 3   | three | 2023-06-20 16:55:04.401217 +00:00 | true  | c                                |
+-----+-------+-----------------------------------+-------+----------------------------------+
```

* Same data, but easier to read and *also works with transposed* data sets.

## Installation

1. Locate the [extractors](extractors/) directory in this repository.
2. Find the script you want to install.
3. Locate the script in the DataGrip settings. [See Add a custom extractor](https://www.jetbrains.com/help/datagrip/data-extractors.html#creating-any-text-extractor-with) for more information.
4. Download or copy the script file into the Datagrip's extractors directory.
