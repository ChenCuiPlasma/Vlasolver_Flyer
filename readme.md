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

## 3. **Simulation Methods and Computing Algorithm**
The phase space(both physical and velocity space) will be discretized into computational mesh. The partial differential equations in the Vlasov-Poisson system will be solved directly on the mesh. While the Vlasov-Poisson system  is a non-linear system, the Vlasov equation itself is a first-order hyperbolic partial differential equation (PDE).  Many numerical schemes have been developed to  solve hyperbolic PDEs.

The methods below are used to discretize the PDEs to numerically solve the Vlasov-Poisson system above.

* Semi-Lagrangian time stepping.
* Third Order Positive Flux Conservation[1] method on phase domain discretization. 

We use this term to describe the capability of handling the phase space dimensions: **xDyV** (x physical domain dimensions and y velocity domain dimensions). 

The code will solve the Vlasov-Poisson system in the following process [2]:

1. Solve the spatial advection equations 
<p align="center"><img src="https://rawgit.com/ChenCuiPlasma/Vlasolver_Flyer/master/svgs/34fa5b6ae77d6ac2f41f1872990baaa5.svg?invert_in_darkmode" align=middle width=116.74574999999999pt height=33.769394999999996pt/></p>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;for half the time step: 
<p align="center"><img src="https://rawgit.com/ChenCuiPlasma/Vlasolver_Flyer/master/svgs/e71d7e34fbbac48cbb5d0ccd0284ef11.svg?invert_in_darkmode" align=middle width=211.7907pt height=16.376943pt/></p>

2. Update the Poisson equation:
<p align="center"><img src="https://rawgit.com/ChenCuiPlasma/Vlasolver_Flyer/master/svgs/627d59d905493b86faf3df59f7e58760.svg?invert_in_darkmode" align=middle width=81.406875pt height=31.913475pt/></p>

3. Solve the acceleration equations:
<p align="center"><img src="https://rawgit.com/ChenCuiPlasma/Vlasolver_Flyer/master/svgs/8fbe7100b85b01a6bd8e8c517baff48a.svg?invert_in_darkmode" align=middle width=117.22523999999999pt height=33.769394999999996pt/></p>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;for the whole time step:
<p align="center"><img src="https://rawgit.com/ChenCuiPlasma/Vlasolver_Flyer/master/svgs/eff8950e906ca672e7d9b8f2ba32c9a0.svg?invert_in_darkmode" align=middle width=165.52304999999998pt height=16.376943pt/></p>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;where the <img src="https://rawgit.com/ChenCuiPlasma/Vlasolver_Flyer/master/svgs/950f751a9d811ec7ce234b576cf977a5.svg?invert_in_darkmode" align=middle width=15.238080000000004pt height=22.598730000000007pt/> is the solution of the characteristics of the acceleration equations.

1. Solve the spatial advection equations 
<p align="center"><img src="https://rawgit.com/ChenCuiPlasma/Vlasolver_Flyer/master/svgs/34fa5b6ae77d6ac2f41f1872990baaa5.svg?invert_in_darkmode" align=middle width=116.74574999999999pt height=33.769394999999996pt/></p>
&nbsp;&nbsp;for half the time step: 
<p align="center"><img src="https://rawgit.com/ChenCuiPlasma/Vlasolver_Flyer/master/svgs/4402889f6676055244687bcf55f8626a.svg?invert_in_darkmode" align=middle width=235.17119999999997pt height=18.269295pt/></p>

## 4. **Current Capabilities Phase Space Dimensions**

* **1D1V** (**Serial** and **Parallel**)
* **2D2V** (with or without external B field both supported, **Serial** and **Parallel**) 

![](./pics/scheme/schematic_vlasov.png)
>*A schematic figure for 2D2V Vlasolver calculation domain*

## 6. **Parallelization**
Vlasolver is currently parallelized by doing domain decomposition  in physical domain. The physical domain is decomposed into local domains and assigned to the corresponding process. Informations are changed and stored in each local domain's guard cells. The velocity is not decomposed now and each process have a full set of velocity space. It is in the plan that in the future the shared-memory parallelization techniques or the heterogeneous computing techniques can be used to parallize the velocity space.

---
## **Reference**
[1] Filbet, F., Sonnendrücker, E. and Bertrand, P., 2001. Conservative numerical schemes for the Vlasov equation. Journal of Computational Physics, 172(1), pp.166-187.

[2] Cheng, C.Z. and Knorr, G., 1976. The integration of the Vlasov equation in configuration space. Journal of Computational Physics, 22(3), pp.330-351.
