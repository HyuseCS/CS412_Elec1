# Week 07 Assignment: Information Gain

## Training data (class attribute: buys_computer)

| RID | age | income | student | credit_rating | buys_computer |
|---|---|---|---|---|---|
| 1 | youth | high | no | fair | no |
| 2 | youth | high | no | excellent | no |
| 3 | middle_aged | high | no | fair | yes |
| 4 | senior | medium | no | fair | yes |
| 5 | senior | low | yes | fair | yes |
| 6 | senior | low | yes | excellent | no |
| 7 | middle_aged | low | yes | excellent | yes |
| 8 | youth | medium | no | fair | no |
| 9 | youth | low | yes | fair | yes |
| 10 | senior | medium | yes | fair | yes |
| 11 | youth | medium | yes | excellent | yes |
| 12 | middle_aged | medium | no | excellent | yes |
| 13 | middle_aged | high | yes | fair | yes |
| 14 | senior | medium | no | excellent | no |

## Formulas

- **Expected information (entropy) of D:** Info(D) = − Σ pᵢ log₂(pᵢ)
- **Expected information after splitting D on attribute A:** Info_A(D) = Σ (|Dⱼ| / |D|) × Info(Dⱼ)
- **Information gain of attribute A:** Gain(A) = Info(D) − Info_A(D)

## Step 1: Expected information of D

D has 14 tuples: 9 yes, 5 no.

Info(D) = − (9/14) log₂(9/14) − (5/14) log₂(5/14)
        = − (0.643)(−0.637) − (0.357)(−1.485)
        = 0.410 + 0.530
        = **0.940 bits**

## a. Gain(income)

| income | count | yes | no |
|---|---|---|---|
| high | 4 | 2 | 2 |
| medium | 6 | 4 | 2 |
| low | 4 | 3 | 1 |

- Info(high) = − (2/4) log₂(2/4) − (2/4) log₂(2/4) = 0.5 + 0.5 = 1.000
- Info(medium) = − (4/6) log₂(4/6) − (2/6) log₂(2/6) = 0.390 + 0.528 = 0.918
- Info(low) = − (3/4) log₂(3/4) − (1/4) log₂(1/4) = 0.311 + 0.500 = 0.811

Info_income(D) = (4/14)(1.000) + (6/14)(0.918) + (4/14)(0.811)
               = 0.286 + 0.393 + 0.232
               = 0.911 bits

Gain(income) = 0.940 − 0.911 = **0.029 bits**

## b. Gain(student)

| student | count | yes | no |
|---|---|---|---|
| yes | 7 | 6 | 1 |
| no | 7 | 3 | 4 |

- Info(yes) = − (6/7) log₂(6/7) − (1/7) log₂(1/7) = 0.191 + 0.401 = 0.592
- Info(no) = − (3/7) log₂(3/7) − (4/7) log₂(4/7) = 0.524 + 0.461 = 0.985

Info_student(D) = (7/14)(0.592) + (7/14)(0.985)
                = 0.296 + 0.493
                = 0.789 bits

Gain(student) = 0.940 − 0.789 = **0.151 bits**

## c. Gain(credit_rating)

| credit_rating | count | yes | no |
|---|---|---|---|
| fair | 8 | 6 | 2 |
| excellent | 6 | 3 | 3 |

- Info(fair) = − (6/8) log₂(6/8) − (2/8) log₂(2/8) = 0.311 + 0.500 = 0.811
- Info(excellent) = − (3/6) log₂(3/6) − (3/6) log₂(3/6) = 0.5 + 0.5 = 1.000

Info_credit_rating(D) = (8/14)(0.811) + (6/14)(1.000)
                      = 0.464 + 0.429
                      = 0.892 bits

Gain(credit_rating) = 0.940 − 0.892 = **0.048 bits**

## Summary

| Attribute | Gain |
|---|---|
| income | 0.029 |
| student | 0.151 |
| credit_rating | 0.048 |

Of these three attributes, **student** has the highest information gain.
