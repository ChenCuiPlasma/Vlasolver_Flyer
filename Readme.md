# **Vlasolver: Grid-Based Kinetic Vlasov Equation Solver**

A high-performance grid-based kinetic Vlasov solver for computational plasma dynamics, main application scopes focus on electric propulsion plasma simulation and space plasma turbulence/instabilities simulation and basic plasma dynamics. This readme file serves to show the outline and preliminary results for this project.

## 1. **Author, Contributor and Maintainer**
* **Author and Maintainer**
          
    Chen Cui (cuichen@usc.edu)

* **Contributor**  
    
    Qiancheng Zhao (qianchez@usc.edu)

## 2. **Models and Equations for Vlasolver**
The model used in this work is a Vlasov-Poisson system which is a kinetic description of the electrostatic collisionless plasma system(with or without the external B field). The Vlasov equation can be written as:
<p align="center">
<img src="https://latex.codecogs.com/gif.latex?\frac{\partial&space;f_\alpha}{\partial&space;t}&plus;\boldsymbol{v}\cdot\nabla_{\boldsymbol{x}}f_{\alpha}&plus;\boldsymbol{a}\cdot\nabla_{\boldsymbol{v}}f_{\alpha}=0" title="\frac{\partial f_\alpha}{\partial t}+\boldsymbol{v}\cdot\nabla_{\boldsymbol{x}}f_{\alpha}+\boldsymbol{a}\cdot\nabla_{\boldsymbol{v}}f_{\alpha}=0" />
</p>
where <img src="https://latex.codecogs.com/gif.latex?f_\alpha(x,&space;v,&space;t)" title="f_\alpha(x, v, t)" /> is the velocity distribution function. The acceleration term  is
<p align="center">
<img src="https://latex.codecogs.com/gif.latex?\boldsymbol{a}=\frac{F_{\alpha}}{m_{\alpha}}=\frac{q_{\alpha}\cdot\boldsymbol{E}&plus;\boldsymbol{v}\times\boldsymbol{B}}{m_{\alpha}}=\frac{-q_{\alpha}\nabla\Phi&plus;\boldsymbol{v}\times\boldsymbol{B}}{m_\alpha}" title="\boldsymbol{a}=\frac{F_{\alpha}}{m_{\alpha}}=\frac{q_{\alpha}\cdot\boldsymbol{E}+\boldsymbol{v}\times\boldsymbol{B}}{m_{\alpha}}=\frac{-q_{\alpha}\nabla\Phi+\boldsymbol{v}\times\boldsymbol{B}}{m_\alpha}" />
</p>
if the external B field is included and it will be written as
<p align="center">
<img src="https://latex.codecogs.com/gif.latex?\boldsymbol{a}=\frac{F_{\alpha}}{m_{\alpha}}=\frac{q_{\alpha}\cdot\boldsymbol{E}}{m_{\alpha}}=\frac{-q_{\alpha}\nabla\Phi}{m_\alpha}" title="\boldsymbol{a}=\frac{F_{\alpha}}{m_{\alpha}}=\frac{q_{\alpha}\cdot\boldsymbol{E}}{m_{\alpha}}=\frac{-q_{\alpha}\nabla\Phi}{m_\alpha}" />
</p>
if the external B field is not included.

The  electric potential. <img src="https://latex.codecogs.com/gif.latex?\Phi" title="\Phi" /> needs to be solved self-consistently  using the Poisson equation
<p align="center">
<img src="https://latex.codecogs.com/gif.latex?\nabla\cdot(\epsilon_0\nabla\Phi)=-e(Z_in_i-n_e)" title="\nabla\cdot(\epsilon_0\nabla\Phi)=-e(Z_in_i-n_e)" />
</p>
where  <img src="https://latex.codecogs.com/gif.latex?Z_i" title="Z_i" />, <img src="https://latex.codecogs.com/gif.latex?n_i" title="n_i" />, and <img src="https://latex.codecogs.com/gif.latex?n_e" title="n_e" /> denote the charge number, ion number density, and electron number density, respectively. 
The macroscopic properties of the plasma are described  by the moments  of the VDF
<p align="center">
<img src="https://latex.codecogs.com/gif.latex?<M_n>=\int_{-\infty}^{\infty}{M_n\hat{f}d\boldsymbol{v}}" title="<M_n>=\int_{-\infty}^{\infty}{M_n\hat{f}d\boldsymbol{v}}" />
</p>

## 3. **Simulation Methods**

