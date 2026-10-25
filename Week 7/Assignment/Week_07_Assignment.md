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

**Expected information (entropy) of D:**

$$Info(D) = -\sum_{i=1}^{m} p_i \log_2(p_i)$$

**Expected information after splitting D on attribute A:**

$$Info_A(D) = \sum_{j=1}^{v} \frac{|D_j|}{|D|} \times Info(D_j)$$

**Information gain of attribute A:**

$$Gain(A) = Info(D) - Info_A(D)$$

## Step 1: Expected information of D

D has 14 tuples: 9 yes, 5 no.

$$
\begin{aligned}
Info(D) &= -\frac{9}{14}\log_2\left(\frac{9}{14}\right) - \frac{5}{14}\log_2\left(\frac{5}{14}\right) \\
&= -(0.643)(-0.637) - (0.357)(-1.485) \\
&= 0.410 + 0.530 \\
&= \mathbf{0.940 \text{ bits}}
\end{aligned}
$$

## a. Gain(income)

| income | count | yes | no |
|---|---|---|---|
| high | 4 | 2 | 2 |
| medium | 6 | 4 | 2 |
| low | 4 | 3 | 1 |

$$Info(high) = -\frac{2}{4}\log_2\left(\frac{2}{4}\right) - \frac{2}{4}\log_2\left(\frac{2}{4}\right) = 0.5 + 0.5 = 1.000$$

$$Info(medium) = -\frac{4}{6}\log_2\left(\frac{4}{6}\right) - \frac{2}{6}\log_2\left(\frac{2}{6}\right) = 0.390 + 0.528 = 0.918$$

$$Info(low) = -\frac{3}{4}\log_2\left(\frac{3}{4}\right) - \frac{1}{4}\log_2\left(\frac{1}{4}\right) = 0.311 + 0.500 = 0.811$$

$$
\begin{aligned}
Info_{income}(D) &= \frac{4}{14}(1.000) + \frac{6}{14}(0.918) + \frac{4}{14}(0.811) \\
&= 0.286 + 0.393 + 0.232 \\
&= 0.911 \text{ bits}
\end{aligned}
$$

$$Gain(income) = 0.940 - 0.911 = \mathbf{0.029 \text{ bits}}$$

## b. Gain(student)

| student | count | yes | no |
|---|---|---|---|
| yes | 7 | 6 | 1 |
| no | 7 | 3 | 4 |

$$Info(yes) = -\frac{6}{7}\log_2\left(\frac{6}{7}\right) - \frac{1}{7}\log_2\left(\frac{1}{7}\right) = 0.191 + 0.401 = 0.592$$

$$Info(no) = -\frac{3}{7}\log_2\left(\frac{3}{7}\right) - \frac{4}{7}\log_2\left(\frac{4}{7}\right) = 0.524 + 0.461 = 0.985$$

$$
\begin{aligned}
Info_{student}(D) &= \frac{7}{14}(0.592) + \frac{7}{14}(0.985) \\
&= 0.296 + 0.493 \\
&= 0.789 \text{ bits}
\end{aligned}
$$

$$Gain(student) = 0.940 - 0.789 = \mathbf{0.151 \text{ bits}}$$

## c. Gain(credit_rating)

| credit_rating | count | yes | no |
|---|---|---|---|
| fair | 8 | 6 | 2 |
| excellent | 6 | 3 | 3 |

$$Info(fair) = -\frac{6}{8}\log_2\left(\frac{6}{8}\right) - \frac{2}{8}\log_2\left(\frac{2}{8}\right) = 0.311 + 0.500 = 0.811$$

$$Info(excellent) = -\frac{3}{6}\log_2\left(\frac{3}{6}\right) - \frac{3}{6}\log_2\left(\frac{3}{6}\right) = 0.5 + 0.5 = 1.000$$

$$
\begin{aligned}
Info_{credit\_rating}(D) &= \frac{8}{14}(0.811) + \frac{6}{14}(1.000) \\
&= 0.464 + 0.429 \\
&= 0.892 \text{ bits}
\end{aligned}
$$

$$Gain(credit\_rating) = 0.940 - 0.892 = \mathbf{0.048 \text{ bits}}$$

## Summary

| Attribute | Gain |
|---|---|
| income | 0.029 |
| student | 0.151 |
| credit_rating | 0.048 |

Of these three attributes, **student** has the highest information gain.
