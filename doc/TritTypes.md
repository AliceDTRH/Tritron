# Trit Types

## Primitives

### Integers:
|   Type  | Trit Count | Byte Size |                                            Value Range                                           |
|:-------:|:----------:|:---------:|:------------------------------------------------------------------------------------------------:|
| Tribble |      3     |     1     |                                           27 [-13, 13]                                           |
|  Tryte  |      6     |     2     |                                          729 [364, -364]                                         |
|  Tshort |     12     |     4     |                                    531,441 [265,720; -265,720]                                   |
|   Tint  |     24     |     8     |                        282,429,536,481 [141,214,768,240; -141,214,768,240]                       |
|  Tlong  |     48     |     16    | 79,766,443,076,872,509,863,361 [39,883,221,538,436,254,931,680; -39,883,221,538,436,254,931,680] |

### Floating point:
|   Type  | Trit Count | Byte Size | Exponent | Mantissa |                  Value Range                 |
|:-------:|:----------:|:---------:|----------|----------|:--------------------------------------------:|
|  Tfloat |     24     |     8     | 6 Trits  | 18 Trit  |         $`±193,710,244 * 3 ^ {±364}`$        |
| Tdouble |     48     |     16    | 12 Trits | 36 Trits | $`±75,047,317,648,499,500 * 3 ^ {±265,720}`$ |

**NOTE**: Tfloat is trit equivelent to Tint, as is Tdouble to Tlong. One can be cast to the other cleanly. <br/>Tfloat <-> Tint; Tdouble <-> Tlong

#### Special floating point values
|      Exponent     | Mantissa |   Interpretation  |
|:-----------------:|:--------:|:-----------------:|
|       e ≠ 0       |   M = 0  |        NAN        |
|      e = MAX      |   M = 0  |     +Infinity     |
|      e = MIN      |   M = 0  |     -Infinity     |
| e = MSB 1, rest 0 |   M = 0  | divide by 0 error |