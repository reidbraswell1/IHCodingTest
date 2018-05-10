# IHCodingTest
IHCodingTest
Search
Message List

## Problem 5

Given three tables (Patients, Hospitals, and Visits), write a SQL query that returns the total number of patients over 65 who visited each hospital in 2017.

### Patients

| `patient_id` | `name`  | `date_of_birth` |
| ------------ | ------- | --------------- |
| 1            | Alice   | 1965-04-02      |
| 2            | Bob     | 1990-08-01      |
| 3            | Charlie | 1982-07-05      |

### Hospitals

| `hospital_id` | `name`    | `city`   |
| ------------- | --------- | -------- |
| 1             | Emory     | Decatur  |
| 2             | Grady     | Atlanta  |
| 3             | Northside | Dunwoody |

### Visits

| `visit_id` | `patient_id` | `hospital_id` | `visit_date` |
| ---------- | ------------ | ------------- | ------------ |
| 1          | 2            | 2             | 2016-05-30   |
| 2          | 1            | 3             | 2016-08-04   |
| 3          | 3            | 3             | 2016-11-22   |
| 4          | 2            | 1             | 2017-01-15   |
| 5          | 1            | 2             | 2017-04-01   |

The result would look something like:

### Results

| Hospital Name | Patients Over 65 |
| ------------- | ---------------- |
| Emory         | 125403           |
| Grady         | 84537            |
| Northside     | 163522           |
