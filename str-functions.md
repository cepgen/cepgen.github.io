---
11;rgb:ffff/ffff/fffftitle: Proton structure functions
---

# Nucleon structure functions

This page presents the list of $F_2/F_L$ parameterisations implemented in `CepGen`.
All of these may be used and linked against any external code.

Structure functions designated with a :warning: sign are only defining $F_2$ and use the $R$ modelling-dependent relation:

$$F_L(\xbj,Q^2) = \left(1+\frac{4m_p^2\xbj^2}{Q^2}\right)\frac{R}{1+R}F_2(\xbj,Q^2).$$


| Name                                 | Code | Description           | $F_2$ | $F_L$ |
|--------------------------------------|:----:|-----------------------|:-----:|:-----:|
| [`SuriYennie`](#suri-yennie)         | 11   |                       | -     | -     |
| `SzczurekUleshchenko`                | 12   |                       | :heavy_check_mark: | -     |
| `BDH`                                | 13   | Block-Durand-Ha       | :heavy_check_mark: | -     |
| [`FioreBrasse`](#fiore-brasse)       | 101  | Fiore & Brasse        | :heavy_check_mark: | -     |
| [`ChristyBosted`](#christy-bosted)   | 102  | Christy & Bosted      | :heavy_check_mark: | :heavy_check_mark: |
| [`ALLM91`](structure-functions/allm) | 201  | ALLM 1991             | :heavy_check_mark: | :warning: |
| [`ALLM97`](structure-functions/allm) | 202  | ALLM 1997             | :heavy_check_mark: | :warning: |
| [`GD07p`](structure-functions/allm)  | 203  | GD07p (HERMES refit)  | :heavy_check_mark: | :warning: |
| [`GD11p`](structure-functions/allm)  | 204  | GD11p (HERMES refit)  | :heavy_check_mark: | :warning: |
| `PDF`

## Suri-Yennie

![](/assets/img/str-fun/suriyennie_f2.png){:width="49%"}
![](/assets/img/str-fun/suriyennie_fl.png){:width="49%"}

## Resonance models
### Fiore-Brasse

![](/assets/img/str-fun/fiorebrasse_f2.png){:width="49%"}
![](/assets/img/str-fun/fiorebrasse_fl.png){:width="49%"}

### Christy-Bosted

![](/assets/img/str-fun/christybosted_f2.png){:width="49%"}
![](/assets/img/str-fun/christybosted_fl.png){:width="49%"}
