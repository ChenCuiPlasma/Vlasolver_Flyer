# **Vlasolver: Grid-Based Kinetic Vlasov Equation Solver**

A high-performance grid-based kinetic Vlasov solver for computational plasma dynamics, main application scopes focus on electric propulsion plasma simulation and space plasma turbulence/instabilities simulation and basic plasma dynamics. This readme file serves to show the outline and preliminary results for this project.

## 1. **Author, Contributor and Maintainer**
* **Author and Maintainer**
          
    Chen Cui (cuichen@usc.edu)

* **Contributor**  
    
    Qiancheng Zhao (qianchez@usc.edu)

## 2. **Models and Equations for Vlasolver**
The model used in this work is a Vlasov-Poisson system which is a kinetic description of the electrostatic collisionless plasma system(with or without the external B field). The Vlasov equation can be written as:
<img src="https://rawgit.com/ChenCuiPlasma/Vlasolver_Flyer (fetch/None/svgs/b167b77e4c9dfb437e32be7483ce87a4.svg?invert_in_darkmode" align=middle width=218.73357pt height=30.588690000000003pt/>
where <img src="https://rawgit.com/ChenCuiPlasma/Vlasolver_Flyer (fetch/None/svgs/4d2163470b670e46b34a53abb5515a21.svg?invert_in_darkmode" align=middle width=68.50305pt height=24.56552999999997pt/> is the velocity distribution function. The acceleration term  is
<p align="center"><img src="https://rawgit.com/ChenCuiPlasma/Vlasolver_Flyer (fetch/None/svgs/4e9c9dc1fcd13167b1b06e538ca9b266.svg?invert_in_darkmode" align=middle width=337.81604999999996pt height=36.0987pt/></p>
if the external B field is included and
<p align="center"><img src="https://rawgit.com/ChenCuiPlasma/Vlasolver_Flyer (fetch/None/svgs/cafed958a96d9b7c88fef7f83b5c1283.svg?invert_in_darkmode" align=middle width=207.52875pt height=36.0987pt/></p>
if the external B field is not included.

The  electric potential. <img src="https://rawgit.com/ChenCuiPlasma/Vlasolver_Flyer (fetch/None/svgs/5e16cba094787c1a10e568c61c63a5fe.svg?invert_in_darkmode" align=middle width=11.827860000000003pt height=22.381919999999983pt/> needs to be solved self-consistently  using the Poisson equation
<p align="center"><img src="https://rawgit.com/ChenCuiPlasma/Vlasolver_Flyer (fetch/None/svgs/e4c23b7c5a4401a89f04a5c6cc37dcff.svg?invert_in_darkmode" align=middle width=201.59535pt height=16.376943pt/></p>
where  <img src="https://rawgit.com/ChenCuiPlasma/Vlasolver_Flyer (fetch/None/svgs/ed35373880183d013fc1bba898b2e3ae.svg?invert_in_darkmode" align=middle width=15.813105000000002pt height=22.381919999999983pt/>, <img src="https://rawgit.com/ChenCuiPlasma/Vlasolver_Flyer (fetch/None/svgs/de3e4ddbaf93c2db6b330ad1998cc995.svg?invert_in_darkmode" align=middle width=14.463570000000002pt height=14.102549999999994pt/>, and <img src="https://rawgit.com/ChenCuiPlasma/Vlasolver_Flyer (fetch/None/svgs/15f7bab95660228710a9c6264a04d9ee.svg?invert_in_darkmode" align=middle width=16.04361pt height=14.102549999999994pt/> denote the charge number, ion number density, and electron number density, respectively. 
The macroscopic properties of the plasma are described  by the moments  of the VDF
<p align="center"><img src="https://rawgit.com/ChenCuiPlasma/Vlasolver_Flyer (fetch/None/svgs/43a1813b0415fff8bef1223496e3815b.svg?invert_in_darkmode" align=middle width=165.8844pt height=39.588615pt/></p>

## 3. **Simulation Methods**

