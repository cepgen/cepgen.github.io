---
title: Structure functions
---

# Nucleon structure functions

This page presents the list of $F_2/F_L$ parameterisations implemented in `CepGen`.
All of these may be used and linked against any external code.

Structure functions designated with a :pencil2: sign are only defining $F_2$ and use the $R$ modelling-dependent relation:

$$F_L(\xbj,Q^2) = \left(1+\frac{4m_p^2\xbj^2}{Q^2}\right)\frac{R}{1+R}F_2(\xbj,Q^2).$$


| Name                                           | Code | Description           | $F_2$ | $F_L$ |
|------------------------------------------------|:----:|-----------------------|:-----:|:-----:|
| [`SuriYennie`](#suri-yennie)                   | 11   |                       | -     | -     |
| [`SzczurekUleshchenko`](#szczurek-uleshchenko) | 12   |                       | :white_check_mark: | -     |
| `BDH`                                          | 13   | Block-Durand-Ha       | :white_check_mark: | -     |
| [`FioreBrasse`](#fiore-brasse)                 | 101  | Fiore & Brasse        | :white_check_mark: | -     |
| [`ChristyBosted`](#christy-bosted)             | 102  | Christy & Bosted      | :white_check_mark: | :white_check_mark: |
| [`ALLM91`](/structure-functions/allm)           | 201  | ALLM 1991             | :white_check_mark: | :pencil2: |
| [`ALLM97`](/structure-functions/allm)           | 202  | ALLM 1997             | :white_check_mark: | :pencil2: |
| [`GD07p`](/structure-functions/allm)            | 203  | GD07p (HERMES refit)  | :white_check_mark: | :pencil2: |
| [`GD11p`](/structure-functions/allm)            | 204  | GD11p (HERMES refit)  | :white_check_mark: | :pencil2: |
| `PDF`

## Suri-Yennie

This set was used as a standard option in the LPAIR event generator.
It provides a reasonable description of SLAC data in the resonance and continuum regions.

![](/assets/img/str-fun/suriyennie_f2.png){:width="49%"}
![](/assets/img/str-fun/suriyennie_fl.png){:width="49%"}

## Szczurek-Uleshchenko

This set [described here](/bibliography#sf:su) puts an emphasis on the low-to-intermediate $Q^2$ region and includes a smooth continuation to low-$Q^2$.

## Resonance models
### Fiore-Brasse

This parameterisation (described [here](/bibliography#sf:fiore) and [here](/bibliography#sf:brasse)) gives a very good description of photoabsorption in the resonance region from low to large $Q^2$.
Furthermore, it is extremely well reproducing JLAB data.

![](/assets/img/str-fun/fiorebrasse_f2.png){:width="49%"}
![](/assets/img/str-fun/fiorebrasse_fl.png){:width="49%"}

### Christy-Bosted

The set [developed by M.E. Christy and P.E. Bosted](/bibliography#sf:cb) is emphasised on the very-low $Q^2$ regime, with its particular use of JLAB's Hall-C data on:
- inclusive inelastic (up to $Q^2\simeq$ 7.5 GeV²),
- photoproduction at $Q^2=0$, and
- DIS data at high-$(Q^2,W)$.

![](/assets/img/str-fun/christybosted_f2.png){:width="49%"}
![](/assets/img/str-fun/christybosted_fl.png){:width="49%"}
