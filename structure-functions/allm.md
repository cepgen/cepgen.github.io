---
title: ALLM structure functions
---

# ALLM nucleon structure functions

A full reference of this parameterisation by _Abramowicz et al._ can be found in [the bibliography](bibliography#abramowicz-et-al).

In this continuum region modelling the $F_2$ proton structure function is parameterised as:

$$F_2(\xbj,Q^2) = \frac{Q^2}{Q^2+m_0^2}\left[F_2^{\Pom}(\xbj,Q^2)+F_2^{\Reg}(\xbj,Q^2)\right]$$

with $m_0$ the effective photon mass. The pomeron/reggeon exchanges terms are parameterised as:

$$F_2^{\Pom,\Reg}(\xbj,Q^2) = c^{\Pom,\Reg}(t) x _ {\Pom,\Reg}^{a^{\Pom,\Reg}(t)} (1-\xbj)^{b^{\Pom,\Reg}(t)}$$

with the slowly-varying function $t = t(Q^2)$ defined as:

$$t(Q^2) = \ln\left(\ln\frac{Q^2+Q_0^2}{\Lambda^2}\right)-\ln\left(\ln\frac{Q_0^2}{\Lambda^2}\right),$$

and the modified Bjorken-$x$ functions:

$$x _ {\Pom,\Reg} = \left(1+\frac{w^2-m_p^2}{Q^2+m _ {\Pom,\Reg}}\right)^{-1}.$$

The six functionals $a^{\Pom,\Reg}(t), b^{\Pom,\Reg}(t), c^{\Pom,\Reg}(t)$ are parameterised as:

$$
a^{\Pom}(t) = a^{\Pom}_1+(a^{\Pom}_1-a^{\Pom}_2)\left[\frac{1}{1+t^{a^{\Pom}_3}}-1\right],\\
b^{\Pom}(t) = b^{\Pom}_1 + b^{\Pom}_2 t^{b^{\Pom}_3},\\
c^{\Pom}(t) = c^{\Pom}_1+(c^{\Pom}_1-c^{\Pom}_2)\left[\frac{1}{1+t^{c^{\Pom}_3}}-1\right]
$$

for the pomeron part, and

$$
a^{\Reg}(t) = a^{\Pom}_1 + a^{\Pom}_2 t^{a^{\Pom}_3},\\
b^{\Reg}(t) = b^{\Pom}_1 + b^{\Pom}_2 t^{b^{\Pom}_3},\\
c^{\Reg}(t) = c^{\Pom}_1 + c^{\Pom}_2 t^{c^{\Pom}_3},\\
$$

for the reggeon subset.

Currently, four tunings of the 23 model parameters are embedded within CepGen:

| Parameter           | Units      | ALLM91   | ALLM97   | GD07p    | GD11p    |
|:-------------------:|:----------:|---------:|---------:|---------:|---------:|
| $m_0^2$             | GeV$^2$    | 0.30508  | 0.31985  | 0.454    | 0.5063   |
| $m _ {\Pom}^2$      | GeV$^2$    | 10.676   | 49.457   | 30.7     | 34.75    |
| $m _ {\Reg}^2$      | GeV$^2$    | 0.20623  | 0.15052  | 0.117    | 0.03190  |
| $Q_0^2$             | GeV$^2$    | 0.27799  | 0.52544  | 1.15     | 1.374    |
| $\Lambda_0^2$       | GeV$^2$    | 0.06527  | 0.06527  | 0.06527  | 0.06527  |
| $a^{\Pom}_1$        | -          | -0.04503 | -0.0808  | -0.105   | -0.11895 |
| $a^{\Pom}_2$        | -          | -0.36407 | -0.44812 | -0.495   | -0.4783  |
| $a^{\Pom}_3$        | -          | 8.17091  | 1.1709   | 1.29     | 1.353    |
| $b^{\Pom}_1$        | -          | 0.49222  | 0.36292  | -1.42    | 1.0833   |
| $b^{\Pom}_2$        | -          | 0.52116  | 1.8917   | 4.51     | 2.656    |
| $b^{\Pom}_3$        | -          | 3.5515   | 1.8439   | 0.551    | 1.771    |
| $c^{\Pom}_1$        | -          | 0.26550  | 0.28067  | 0.339    | 0.3638   |
| $c^{\Pom}_2$        | -          | 0.04856  | 0.22291  | 0.127    | 0.1211   |
| $c^{\Pom}_3$        | -          | 1.04682  | 2.1979   | 1.16     | 1.166    |
| $a^{\Reg}_1$        | -          | 0.60408  | 0.584    | 0.374    | 0.3425   |
| $a^{\Reg}_2$        | -          | 0.17353  | 0.37888  | 0.998    | 1.0603   |
| $a^{\Reg}_3$        | -          | 1.61812  | 2.6063   | 0.775    | 0.5164   |
| $b^{\Reg}_1$        | -          | 1.26066  | 0.01147  | 2.71     | -10.408  |
| $b^{\Reg}_2$        | -          | 1.83624  | 3.7582   | 1.83     | 14.857   |
| $b^{\Reg}_3$        | -          | 0.81141  | 0.49338  | 1.26     | 0.07739  |
| $c^{\Reg}_1$        | -          | 0.67639  | 0.80107  | 0.838    | 1.3633   |
| $c^{\Reg}_2$        | -          | 0.49027  | 0.97307  | 2.36     | 2.256    |
| $c^{\Reg}_3$        | -          | 2.66275  | 3.4942   | 1.77     | 2.209    |

The ALLM91 tuning is fitted from all pre-HERA data points available.

![](/assets/img/str-fun/allm91_f2.png){:width="49%"}
![](/assets/img/str-fun/allm91_fl.png){:width="49%"}
![](/assets/img/str-fun/allm97_f2.png){:width="49%"}
![](/assets/img/str-fun/allm97_fl.png){:width="49%"}
![](/assets/img/str-fun/gd07p_f2.png){:width="49%"}
![](/assets/img/str-fun/gd07p_fl.png){:width="49%"}
![](/assets/img/str-fun/gd11p_f2.png){:width="49%"}
![](/assets/img/str-fun/gd11p_fl.png){:width="49%"}


