---
description: >-
  Test cases for working with test terminals in a production environment The
  answer depends on the value of the coins specified in the coinAmount parameter
---

# Test cases

| Operation    | The number of cents | Response |
| ------------ | ------------------- | -------- |
| SALES step 2 | 4 cents             | SUCCESS  |
| SALES step 2 | 5 cents             | FAIL     |
| SALES step 2 | 6 cents             | FAIL     |
| С2А step 2   | 10 cents            | SUCCESS  |
| С2А step 2   | 11 cents            | FAIL     |
| С2А step 2   | 12 cents            | FAIL     |
| А2С          | 13 cents            | SUCCESS  |
| А2С          | 14 cents            | FAIL     |
| А2С          | 15 cents            | FAIL     |
| REFUND       | 16 cents            | SUCCESS  |
| REFUND       | 17 cents            | FAIL     |
| REFUND       | 18 cents            | FAIL     |
