---
title: Proton structure functions
---

# Proton structure functions

## Compact list of parameterisations

| Name                   | Code | Description           | $F_2$ | $F_L$ |
|------------------------|:----:|-----------------------|:-----:|:-----:|
| `Suri-Yennie`          | 11   |                       | -     | -     |
| `Szczurek-Uleshchenko` | 12   |                       | :ballot_box_with_check:  | -     |
| `BDH`                  | 13   | Block-Durand-Ha       | :ballot_box_with_check:  | -     |
| `Fiore-Brasse`         | 101  | Fiore & Brasse        | :ballot_box_with_check:  | -     |
| `Christy-Bosted`       | 102  | Christy & Bosted      | :ballot_box_with_check:  | :ballot_box_with_check:  |
| `ALLM;91`              | 201  | ALLM 1991             | :ballot_box_with_check:  | :eight_pointed_black_star:  |
| `ALLM;97`              | 202  | ALLM 1997             | :ballot_box_with_check:  | :eight_pointed_black_star:  |
| `GD07p`                | 203  | GD07p (HERMES refit)  | :ballot_box_with_check:  | :eight_pointed_black_star:  |
| `GD11p`                | 204  | GD11p (HERMES refit)  | :ballot_box_with_check:  | :eight_pointed_black_star:  |

## Suri-Yennie

## Resonance models
### Fiore-Brasse

### Christy-Bosted

## Abramowicz et al

A full reference of this parameterisation can be found in [the bibliography](bibliography#abramowicz-et-al).

In this continuum region modelling the $F_2$ proton structure function is parameterised as:

$$F_2(Q^2,x _ {\mathrm{Bj}}) = \frac{Q^2}{Q^2+m_0^2}\left[F_2^{\mathbb P}(Q^2,x _ {\mathrm{Bj}})+F_2^{\mathbb R}(Q^2,x _ {\mathrm{Bj}})\right]$$

with $m_0$ the effective photon mass. The pomeron/reggeon exchanges terms are parameterised as:

$$F_2^{\mathbb P,\mathbb R}(Q^2,x _ {\mathrm{Bj}}) = c^{\mathbb P,\mathbb R}(t) x _ {\mathbb P,\mathbb R}^{a^{\mathbb P,\mathbb R}(t)} (1-x _ {\mathrm{Bj}})^{b^{\mathbb P,\mathbb R}(t)}$$

with the slowly-varying function $t = t(Q^2)$ defined as:

$$t(Q^2) = \ln\left(\ln\frac{Q^2+Q_0^2}{\Lambda^2}\right)-\ln\left(\ln\frac{Q_0^2}{\Lambda^2}\right),$$

and the modified Bjorken-$x$ functions:

$$x _ {\mathbb P,\mathbb R} = \left(1+\frac{w^2-m_p^2}{Q^2+m _ {\mathbb P,\mathbb R}}\right)^{-1}.$$

The six functionals $a^{\mathbb P,\mathbb R}(t), b^{\mathbb P,\mathbb R}(t), c^{\mathbb P,\mathbb R}(t)$ are parameterised as:

$$
a^{\mathbb P}(t) = a^{\mathbb P}_1+(a^{\mathbb P}_1-a^{\mathbb P}_2)\left[\frac{1}{1+t^{a^{\mathbb P}_3}}-1\right],\\
b^{\mathbb P}(t) = b^{\mathbb P}_1 + b^{\mathbb P}_2 t^{b^{\mathbb P}_3},\\
c^{\mathbb P}(t) = c^{\mathbb P}_1+(c^{\mathbb P}_1-c^{\mathbb P}_2)\left[\frac{1}{1+t^{c^{\mathbb P}_3}}-1\right]
$$

for the pomeron part, and

$$
a^{\mathbb R}(t) = a^{\mathbb P}_1 + a^{\mathbb P}_2 t^{a^{\mathbb P}_3},\\
b^{\mathbb R}(t) = b^{\mathbb P}_1 + b^{\mathbb P}_2 t^{b^{\mathbb P}_3},\\
c^{\mathbb R}(t) = c^{\mathbb P}_1 + c^{\mathbb P}_2 t^{c^{\mathbb P}_3},\\
$$

for the reggeon functionals.

Currently, four tunings of the 23 model parameters are embedded within CepGen:

| Parameter           | Units      | ALLM91   | ALLM97   | GD07p    | GD11p    |
|:-------------------:|:----------:|---------:|---------:|---------:|---------:|
| $m_0^2$             | GeV$^2$    | 0.30508  | 0.31985  | 0.454    | 0.5063   |
| $m _ {\mathbb P}^2$ | GeV$^2$    | 10.676   | 49.457   | 30.7     | 34.75    |
| $m _ {\mathbb R}^2$ | GeV$^2$    | 0.20623  | 0.15052  | 0.117    | 0.03190  |
| $Q_0^2$             | GeV$^2$    | 0.27799  | 0.52544  | 1.15     | 1.374    |
| $\Lambda_0^2$       | GeV$^2$    | 0.06527  | 0.06527  | 0.06527  | 0.06527  |
| $a^{\mathbb P}_1$   | -          | -0.04503 | -0.0808  | -0.105   | -0.11895 |
| $a^{\mathbb P}_2$   | -          | -0.36407 | -0.44812 | -0.495   | -0.4783  |
| $a^{\mathbb P}_3$   | -          | 8.17091  | 1.1709   | 1.29     | 1.353    |
| $b^{\mathbb P}_1$   | -          | 0.49222  | 0.36292  | -1.42    | 1.0833   |
| $b^{\mathbb P}_2$   | -          | 0.52116  | 1.8917   | 4.51     | 2.656    |
| $b^{\mathbb P}_3$   | -          | 3.5515   | 1.8439   | 0.551    | 1.771    |
| $c^{\mathbb P}_1$   | -          | 0.26550  | 0.28067  | 0.339    | 0.3638   |
| $c^{\mathbb P}_2$   | -          | 0.04856  | 0.22291  | 0.127    | 0.1211   |
| $c^{\mathbb P}_3$   | -          | 1.04682  | 2.1979   | 1.16     | 1.166    |
| $a^{\mathbb R}_1$   | -          | 0.60408  | 0.584    | 0.374    | 0.3425   |
| $a^{\mathbb R}_2$   | -          | 0.17353  | 0.37888  | 0.998    | 1.0603   |
| $a^{\mathbb R}_3$   | -          | 1.61812  | 2.6063   | 0.775    | 0.5164   |
| $b^{\mathbb R}_1$   | -          | 1.26066  | 0.01147  | 2.71     | -10.408  |
| $b^{\mathbb R}_2$   | -          | 1.83624  | 3.7582   | 1.83     | 14.857   |
| $b^{\mathbb R}_3$   | -          | 0.81141  | 0.49338  | 1.26     | 0.07739  |
| $c^{\mathbb R}_1$   | -          | 0.67639  | 0.80107  | 0.838    | 1.3633   |
| $c^{\mathbb R}_2$   | -          | 0.49027  | 0.97307  | 2.36     | 2.256    |
| $c^{\mathbb R}_3$   | -          | 2.66275  | 3.4942   | 1.77     | 2.209    |

The ALLM91 tuning is fitted from all pre-HERA data points available.

