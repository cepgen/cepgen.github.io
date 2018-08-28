---
title: Proton structure functions
---

# Proton structure functions

## Compact list of parameterisations

| Name                               | Code | Description           | $F_2$ | $F_L$ |
|------------------------------------|:----:|-----------------------|:-----:|:-----:|
| [`SuriYennie`](#suri-yennie)       | 11   |                       | -     | -     |
| `SzczurekUleshchenko`              | 12   |                       | :ballot_box_with_check:  | -     |
| `BDH`                              | 13   | Block-Durand-Ha       | :ballot_box_with_check:  | -     |
| [`FioreBrasse`](#fiore-brasse)     | 101  | Fiore & Brasse        | :ballot_box_with_check:  | -     |
| [`ChristyBosted`](#christy-bosted) | 102  | Christy & Bosted      | :ballot_box_with_check:  | :ballot_box_with_check:  |
| [`ALLM91`](#abramowicz-et-al)      | 201  | ALLM 1991             | :ballot_box_with_check:  | :eight_pointed_black_star:  |
| [`ALLM97`](#abramowicz-et-al)      | 202  | ALLM 1997             | :ballot_box_with_check:  | :eight_pointed_black_star:  |
| [`GD07p`](#abramowicz-et-al)       | 203  | GD07p (HERMES refit)  | :ballot_box_with_check:  | :eight_pointed_black_star:  |
| [`GD11p`](#abramowicz-et-al)       | 204  | GD11p (HERMES refit)  | :ballot_box_with_check:  | :eight_pointed_black_star:  |

Structure functions having a :eight_pointed_black_star: in the $F_L$ are only defining $F_2$ and use the $R$ modelling-dependent relation:

$$F_L(x_{\rm Bj}, Q^2) = \left(1+\frac{4m_p^2x_{\rm Bj}^2}{Q^2}\right)\frac{R}{1+R}F_2(x_{\rm Bj}, Q^2).$$

## Suri-Yennie

## Resonance models
### Fiore-Brasse

### Christy-Bosted

## Abramowicz et al

A full reference of this parameterisation can be found in [the bibliography](bibliography#abramowicz-et-al).

In this continuum region modelling the $F_2$ proton structure function is parameterised as:

$$F_2(x _ {\mathrm{Bj},Q^2}) = \frac{Q^2}{Q^2+m_0^2}\left[F_2^{I\!P}(Q^2,x _ {\mathrm{Bj}})+F_2^{I\!R}(Q^2,x _ {\mathrm{Bj}})\right]$$

with $m_0$ the effective photon mass. The pomeron/reggeon exchanges terms are parameterised as:

$$F_2^{I\!P,I\!R}(x _ {\mathrm{Bj}}, Q^2) = c^{I\!P,I\!R}(t) x _ {I\!P,I\!R}^{a^{I\!P,I\!R}(t)} (1-x _ {\mathrm{Bj}})^{b^{I\!P,I\!R}(t)}$$

with the slowly-varying function $t = t(Q^2)$ defined as:

$$t(Q^2) = \ln\left(\ln\frac{Q^2+Q_0^2}{\Lambda^2}\right)-\ln\left(\ln\frac{Q_0^2}{\Lambda^2}\right),$$

and the modified Bjorken-$x$ functions:

$$x _ {I\!P,I\!R} = \left(1+\frac{w^2-m_p^2}{Q^2+m _ {I\!P,I\!R}}\right)^{-1}.$$

The six functionals $a^{I\!P,I\!R}(t), b^{I\!P,I\!R}(t), c^{I\!P,I\!R}(t)$ are parameterised as:

$$
a^{I\!P}(t) = a^{I\!P}_1+(a^{I\!P}_1-a^{I\!P}_2)\left[\frac{1}{1+t^{a^{I\!P}_3}}-1\right],\\
b^{I\!P}(t) = b^{I\!P}_1 + b^{I\!P}_2 t^{b^{I\!P}_3},\\
c^{I\!P}(t) = c^{I\!P}_1+(c^{I\!P}_1-c^{I\!P}_2)\left[\frac{1}{1+t^{c^{I\!P}_3}}-1\right]
$$

for the pomeron part, and

$$
a^{I\!R}(t) = a^{I\!P}_1 + a^{I\!P}_2 t^{a^{I\!P}_3},\\
b^{I\!R}(t) = b^{I\!P}_1 + b^{I\!P}_2 t^{b^{I\!P}_3},\\
c^{I\!R}(t) = c^{I\!P}_1 + c^{I\!P}_2 t^{c^{I\!P}_3},\\
$$

for the reggeon functionals.

Currently, four tunings of the 23 model parameters are embedded within CepGen:

| Parameter           | Units      | ALLM91   | ALLM97   | GD07p    | GD11p    |
|:-------------------:|:----------:|---------:|---------:|---------:|---------:|
| $m_0^2$             | GeV$^2$    | 0.30508  | 0.31985  | 0.454    | 0.5063   |
| $m _ {I\!P}^2$      | GeV$^2$    | 10.676   | 49.457   | 30.7     | 34.75    |
| $m _ {I\!R}^2$      | GeV$^2$    | 0.20623  | 0.15052  | 0.117    | 0.03190  |
| $Q_0^2$             | GeV$^2$    | 0.27799  | 0.52544  | 1.15     | 1.374    |
| $\Lambda_0^2$       | GeV$^2$    | 0.06527  | 0.06527  | 0.06527  | 0.06527  |
| $a^{I\!P}_1$        | -          | -0.04503 | -0.0808  | -0.105   | -0.11895 |
| $a^{I\!P}_2$        | -          | -0.36407 | -0.44812 | -0.495   | -0.4783  |
| $a^{I\!P}_3$        | -          | 8.17091  | 1.1709   | 1.29     | 1.353    |
| $b^{I\!P}_1$        | -          | 0.49222  | 0.36292  | -1.42    | 1.0833   |
| $b^{I\!P}_2$        | -          | 0.52116  | 1.8917   | 4.51     | 2.656    |
| $b^{I\!P}_3$        | -          | 3.5515   | 1.8439   | 0.551    | 1.771    |
| $c^{I\!P}_1$        | -          | 0.26550  | 0.28067  | 0.339    | 0.3638   |
| $c^{I\!P}_2$        | -          | 0.04856  | 0.22291  | 0.127    | 0.1211   |
| $c^{I\!P}_3$        | -          | 1.04682  | 2.1979   | 1.16     | 1.166    |
| $a^{I\!R}_1$        | -          | 0.60408  | 0.584    | 0.374    | 0.3425   |
| $a^{I\!R}_2$        | -          | 0.17353  | 0.37888  | 0.998    | 1.0603   |
| $a^{I\!R}_3$        | -          | 1.61812  | 2.6063   | 0.775    | 0.5164   |
| $b^{I\!R}_1$        | -          | 1.26066  | 0.01147  | 2.71     | -10.408  |
| $b^{I\!R}_2$        | -          | 1.83624  | 3.7582   | 1.83     | 14.857   |
| $b^{I\!R}_3$        | -          | 0.81141  | 0.49338  | 1.26     | 0.07739  |
| $c^{I\!R}_1$        | -          | 0.67639  | 0.80107  | 0.838    | 1.3633   |
| $c^{I\!R}_2$        | -          | 0.49027  | 0.97307  | 2.36     | 2.256    |
| $c^{I\!R}_3$        | -          | 2.66275  | 3.4942   | 1.77     | 2.209    |

The ALLM91 tuning is fitted from all pre-HERA data points available.
