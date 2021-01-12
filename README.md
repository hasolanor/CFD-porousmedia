# Transport and retention of chemical scalars in porous media: a 2D CFD-based study at the pore-scale
Hillmert A. Solano, Faculty of Mines, Universidad Nacional de Colombia
## Presentation (video)

## 1. Introduction
The injection of taylored solutions with chemical scalars, such as polymers, surfactants, nanoparticles, salts;  is common in subsurface engineering applications. In hydrocarbon reservoirs, chemical scalars are injected to generate or favour different interactions that improve oil and gas production. On other vein, in Geological Carbon Sequestration (GCS), some studies have shown that scalars allows to increase carbon storage capacity in these operations. Additionally, chemical scalars are used to remove NAPL and solid pollulants from soil and groundwater bodies.

When a chemical scalar is injected into a porous medium, it follows some transport and retention dynamics by the interactions among other scalar particles/molecules (aggregation and disaggregation), the carrier fluid (transport phenomena), and the solid surface (surface phenomena), which govern its deployment. Hence, the understanding of the transport and retention dynamics allows to evaluate chemical species behaviour inside the porous medium, and therefore determine the most favourables conditions targeting better outcomes.

## 2. Methodology
In order to address transport and retention dynamic of passive scalars in porous media at the pore-scale, a CFD framework is proposed. 

### Problem Statement




### Mathematical Formulation

#### Incompressible flow

In the first hand, Navier-Stokes set of equations are used to model the fluid flow through the porous medium. By this approach, steady flow is considered, so the transient term is neglected. For a 2D problem, this is formed by 3 equations: one for fluid continuity and two for fluid momentum balance (one per dimension). By these equations, pressure and velocity distributions can be estimated for the spatial domain.

<img src="https://render.githubusercontent.com/render/math?math=\Large {\frac{\partial u_x}{\partial x}}%2B{\frac{\partial u_y}{\partial y}}=0">

<img src="https://render.githubusercontent.com/render/math?math=\Large u_x \frac{\partial u_x}{\partial x}%2B u_y \frac{\partial u_x}{\partial y}-\nu \left( \frac{\partial^2 u_x}{\partial x^2} %2B \frac{\partial^2 u_x}{\partial y^2} \right) %2B \frac{1}{\rho} \frac{\partial P}{\partial x}=0">

<img src="https://render.githubusercontent.com/render/math?math=\Large u_x \frac{\partial u_y}{\partial x}%2B u_y \frac{\partial u_y}{\partial y}-\nu \left( \frac{\partial^2 u_y}{\partial x^2}%2B \frac{\partial^2 u_y}{\partial y^2} \right) %2B \frac{1}{\rho} \frac{\partial P}{\partial y}=0">

In order to delimite the mathematical problem regarding incompressible flow, initial and boundary conditions are proposed based on the problem statement. As an initial condition, zero velocity and a constant pressure are considered.

<img src="https://render.githubusercontent.com/render/math?math=\Large u_x (t=0)=0, u_y (t=0)=0, P (t=0)=P_{out}">

At the inlet boundary, constant velocity and pressure zero grandient are considered.

<img src="https://render.githubusercontent.com/render/math?math=\Large \frac{\partial P}{\partial x} |_{\small \textrm{inlet}}=0, u_x|_{\small \textrm{inlet}}=u_{in}, u_y|_{\small \textrm{inlet}}=0">

Although, at the outlet boundary, constant pressure and velocity zero gradient, corresponding to an outlow-type condition. 

<img src="https://render.githubusercontent.com/render/math?math=\Large P|_{\small \textrm{outlet}}=P_{out}, \frac{\partial u_x}{\partial x}|_{\small \textrm{outlet}}=0, \frac{\partial u_y}{\partial x}|_{\small \textrm{outlet}}=0">

For the grains boundary, a non-slip condition is considered. In this, 

<img src="https://render.githubusercontent.com/render/math?math=\Large \frac{\partial P}{\partial x}|_{\small \textrm{grain}}=0, u_x|_{\small \textrm{grain}}=0, u_y|_{\small \textrm{grain}}=0">

Finally, for the top and bottom boundary, a symetry 

#### Chemical scalar transport
On the other hand, chemical scalar transport are modelled by the unsteady Advection-Diffusion (ADR) equation. By this equation, and with a predefined velocity field, the concentration field can be computed.

<img src="https://render.githubusercontent.com/render/math?math=\Large \frac{\partial c}{\partial t}-\left(u_x \frac{\partial c}{\partial x} %2B u_y \frac{\partial c}{\partial x} \right) %2B D \left( \frac{\partial^2 c}{\partial x^2} %2B \frac{\partial^2 c}{\partial y^2}\right)=0">

As boundary conditions. 
This condition corresponds to the Langmuir-type retention model, which is widely used in these applications.

<img src="https://render.githubusercontent.com/render/math?math=\Large c(t=0)=c_{in}">


<img src="https://render.githubusercontent.com/render/math?math=\Large c=c_{in}">
<img src="https://render.githubusercontent.com/render/math?math=\Large \frac{\partial c}{\partial x}=0">
<img src="https://render.githubusercontent.com/render/math?math=\Large -D\left( \frac{\partial^2 c}{\partial x^2} %2B \frac{\partial^2 c}{\partial y^2}\right) = K_a \left( 1-\frac{s}{s_{max}} \right)c - K_d s">

### Dimensionless variables

| Dimensionless | Definition | Description |
| ------------- | ------------- | ------------- |
| <img src="https://render.githubusercontent.com/render/math?math=\Large N_{Pe}">  | <img src="https://render.githubusercontent.com/render/math?math=\Large \frac{u_{in}L}{D}">  | Contenido de la celda  |
| <img src="https://render.githubusercontent.com/render/math?math=\Large N_{Pe}">  | <img src="https://render.githubusercontent.com/render/math?math=\Large \frac{u_{in}L}{D}">  | Contenido de la celda  |
| <img src="https://render.githubusercontent.com/render/math?math=\Large N_{Pe}">  | <img src="https://render.githubusercontent.com/render/math?math=\Large \frac{u_{in}L}{D}">  | Contenido de la celda  |
| <img src="https://render.githubusercontent.com/render/math?math=\Large N_{Da}">  | <img src="https://render.githubusercontent.com/render/math?math=\Large \frac{K_aL^2}{D}">  | Contenido de la celda  |



### Meshing and solution schemes



## 3. Results

## 4. Conclusions

## 5. References


## Appendix A. Mesh independence study

## Appendix B. Model Validation

## Appendix C. Convergence Evaluation

## Appendix D. 
