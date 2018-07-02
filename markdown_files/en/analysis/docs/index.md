<!-- 表記は FrontISTR ver. 0.0 で統一します -->
# FrontISTR Theory Manual

This software is the outcome of "Research and Development of Innovative Simulation Software" project supported by Research and Development for Next-generation Information Technology of Ministry of Education, Culture, Sports, Science and Technology. We assume that you agree with our license agreement of "MIT License" by using this software either for the purpose of profit-making business or for free of charge. This software is protected by the copyright law and the other related laws, regarding unspecified issues in our license agreement and contact, or condition without either license agreement or contact.

<img src="./image/FrontISTR_logo.png" width="350px">

| 項目 | 説明 |
|:---------:|:---------|
| Name of Software | FrontISTR |
| Version | 5.0 |
| License | MIT License |
| Correnponding Clerks | FrontISTR Commons<br>2-11-16 Yayoi, Bunkyo-ku, Tokyo<br>(東京大学大学院工学系研究科 総合研究機構内)<br>E-mail：fstr_seminar@multi.k.u-tokyo.ac.jp |

## Manuals

  - [Introduction]()
  - [How to install]()
  - [Theory]()
  - [User's manual]()
  - [Tutorial]()

<!-- ここまでテンプレート -->
---

This manual describes the analysis method by the finite element method (FEM) used in FrontISTR. 

Regarding the stress analysis method of solids, the infinitesimal deformation linear elasticity static analyais method is described first, and geometric nonlinear analysis method and elastoplasticity analysis method which are required when handling finite deformation problems are described next. Furthermore, a summarized evaluation method of the facture mechanics parameters which can be acquired using the results of the stress analysis by FEM is described. Finally, th eigenvalue analysis and heat conduction analysis method is described.

## List of description on this manual

- [Analysis Flow](./analysis_01)
- [Input File](./analysis_01)
    - [Overall Control Data](./analysis_02)
    - [Mesh Partitioning Data](./analysis_03)
    - [Mesh Data](./analysis_04)
    - [Analysis Control Data](./analysis_05)
    - [Visualization Control Data](./analysis_05)
- [Output File](./analysis_01)
    - [Log Data](./analysis_05)
    - [Restart Data](./analysis_05)
    - [Visualization Data](./analysis_05)
- [Element Library](./analysis_06)
- [Material Data](./analysis_07)
- [User Subroutines](./analysis_08)
