# **Vlasolver: Grid-Based Kinetic Vlasov Equation Solver**

A high-performance grid-based kinetic Vlasov solver for computational plasma dynamics, main application scopes focus on electric propulsion plasma simulation and space plasma turbulence/instabilities simulation and basic plasma dynamics. This readme file serves to show the outline and preliminary results for this project.

## 1. **Author, Contributor and Maintainer**
* **Author and Maintainer**
          
    Chen Cui (cuichen@usc.edu)

* **Contributor**  
    
    Qiancheng Zhao (qianchez@usc.edu)

## 2. **Models and Equations for Vlasolver**
The model used in this work is a Vlasov-Poisson system which is a kinetic description of the electrostatic collisionless plasma system(with or without the external B field). The Vlasov equation can be written as:
<p align="center"><img src="https://rawgit.com/ChenCuiPlasma/Vlasolver_Flyer/master/svgs/e71a173cc8644e32041f22b26ed65be0.svg?invert_in_darkmode" align=middle width=223.32420000000002pt height=33.769394999999996pt/></p>
The acceleration term  is
<p align="center"><img src="https://rawgit.com/ChenCuiPlasma/Vlasolver_Flyer/master/svgs/4e9c9dc1fcd13167b1b06e538ca9b266.svg?invert_in_darkmode" align=middle width=337.81604999999996pt height=36.0987pt/></p>
if the external B field is included and
<p align="center"><img src="https://rawgit.com/ChenCuiPlasma/Vlasolver_Flyer/master/svgs/cafed958a96d9b7c88fef7f83b5c1283.svg?invert_in_darkmode" align=middle width=207.52875pt height=36.0987pt/></p>
if the external B field is not included.

The  electric potential. <img src="https://rawgit.com/ChenCuiPlasma/Vlasolver_Flyer/master/svgs/5e16cba094787c1a10e568c61c63a5fe.svg?invert_in_darkmode" align=middle width=11.827860000000003pt height=22.381919999999983pt/> needs to be solved self-consistently  using the Poisson equation
<p align="center"><img src="https://rawgit.com/ChenCuiPlasma/Vlasolver_Flyer/master/svgs/e4c23b7c5a4401a89f04a5c6cc37dcff.svg?invert_in_darkmode" align=middle width=201.59535pt height=16.376943pt/></p> 
The macroscopic properties of the plasma are described  by the moments  of the VDF
<p align="center"><img src="https://rawgit.com/ChenCuiPlasma/Vlasolver_Flyer/master/svgs/43a1813b0415fff8bef1223496e3815b.svg?invert_in_darkmode" align=middle width=165.8844pt height=39.588615pt/></p>

## 3. **Simulation Methods**