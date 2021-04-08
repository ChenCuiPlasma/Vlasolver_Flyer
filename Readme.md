# **Vlasolver: Grid-Based Kinetic Vlasov Equation Solver**

A high-performance grid-based kinetic Vlasov solver for computational plasma dynamics, main application scopes focus on electric propulsion plasma simulation and space plasma turbulence/instabilities simulation and basic plasma dynamics. This readme file serves to show the outline and preliminary results for this project.

## 1. **Author, Contributor and Maintainer**
* **Author and Maintainer**
          
    Chen Cui (cuichen@usc.edu)

* **Contributor**  
    
    Qiancheng Zhao (qianchez@usc.edu)

## 2. **Models and Equations for Vlasolver**
The model used in this work is a Vlasov-Poisson system which is a kinetic description of the electrostatic collisionless plasma system(with or without the external B field). The Vlasov equation can be written as:
$$
\frac{\partial f_\alpha}{\partial t}+\boldsymbol{v}\cdot\nabla_{\boldsymbol{x}}f_{\alpha}+\boldsymbol{a}\cdot\nabla_{\boldsymbol{v}}f_{\alpha}=0
$$
where $f_\alpha(x, v, t)$ is the velocity distribution function. The acceleration term  is
$$
\boldsymbol{a}=\frac{F_{\alpha}}{m_{\alpha}}=\frac{q_{\alpha}\cdot\boldsymbol{E}+\boldsymbol{v}\times\boldsymbol{B}}{m_{\alpha}}=\frac{-q_{\alpha}\nabla\Phi+\boldsymbol{v}\times\boldsymbol{B}}{m_\alpha}
$$
if the external B field is included and
$$
\boldsymbol{a}=\frac{F_{\alpha}}{m_{\alpha}}=\frac{q_{\alpha}\cdot\boldsymbol{E}}{m_{\alpha}}=\frac{-q_{\alpha}\nabla\Phi}{m_\alpha}
$$
if the external B field is not included.

The  electric potential. $\Phi$ needs to be solved self-consistently  using the Poisson equation
$$
\nabla\cdot(\epsilon_0\nabla\Phi)=-e(Z_in_i-n_e)
$$
where  $Z_i$, $n_i$, and $n_e$ denote the charge number, ion number density, and electron number density, respectively. 
The macroscopic properties of the plasma are described  by the moments  of the VDF
$$
<M_n>=\int_{-\infty}^{\infty}{M_n\hat{f}d\boldsymbol{v}}
$$

## 3. **Simulation Methods**

