
Assignment_7 notebook : Enas architecture

Below receptive field calculation of GoogleNet.

Initially we have:

|input size | Receptive field |J0|
|-----------|-----------------|--|
|224 |1|1|

By by calculation, we have below:


| OPERATION   |      KERNEL SIZE      |  STRIDE | RECEPTIVE FIELD | J_OUT|
|-------------|-------------|---------|---------|---------|
| CON |  7 | 2 |7  |2|
| MAX |  3 | 2 |11 |4|
| CON |  1 | 1 |19 |4|
| INCEP_1_CON |  1 | 1 |27 |8|
| INCEP_1_CON |  5 | 1 |59 |8|
| INCEP_2_CON |  1 | 1 |59 |8|
| INCEP_2_CON |  5 | 1 |91 |8|
| MAX |  3 | 2 |107 |16|
| INCEP_3_CON |  1 | 1 |107 |16|
| INCEP_3_CON |  5 | 1 |171 |16|
| INCEP_4_CON |  1 | 1 |171 |16|
| INCEP_4_CON |  5 | 1 |235 |16|
| INCEP_5_CON |  1 | 1 |235 |16|
| INCEP_5_CON |  5 | 1 |299 |16|
| INCEP_6_CON |  1 | 1 |299 |16|
| INCEP_6_CON |  5 | 1 |363 |16|
| INCEP_7_CON |  1 | 1 |363 |16|
| INCEP_7_CON |  5 | 1 |427 |16|
| MAX |  3 | 2 |459 |32|
| INCEP_8_CON |  1 | 1 |459 |32|
| INCEP_8_CON |  5 | 1 |587 |32|
| INCEP_8_CON |  1 | 1 |587 |32|
| INCEP_8_CON |  5 | 1 |715 |32|




