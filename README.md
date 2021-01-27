# Chemical scalars transport in porous media: a 2D CFD study at the pore-scale
Hillmert A. Solano, Faculty of Mines, Universidad Nacional de Colombia
## Presentation (video)



## 1. Introduction
The injection of tailored solutions with chemical scalars; such as polymers, surfactants, nanoparticles, salts, and others;  has become very common in subsurface engineering applications. The Enhanced Oil Recovery (EOR) operations are a good example of these applications, in which chemical scalars use to be injected to generate or favour different interactions that improve oil and gas production. On another vein, the remotion of non-aqueous liquid phases (NAPL) and solid pollutants from soil and groundwater bodies can be improved using chemical scalars. Furthermore, recent studies show a positive impact on the carbon dioxide storage capacity when a Geological Carbon Sequestration (GCS) operation is upgraded by the use of chemical scalars. All above accounts for the importance of the study of chemical scalar behaviour in porous media targeting to improving its understanding and the design process of these operations.

One of the most important issues involved in the behaviour of chemica scalars in porous media are the transport phenomena. When a chemical scalar is injected into a porous medium, several transport mechanisms are followed. These mechanisms are strongly associated with its interactions with other scalar particles/molecules, the carrier fluid, and the solid surface; and govern its deployment inside the porous medium. With this in mind, a proper representation of the transport dynamics exhibed by the chemical scalars inside the porous media is key to design a subsurface engineering application involving chemical scalars.

This work is focused on the phenomenological study of transport dynamics followed by chemical scalars in porous media. In order to address this objective, a CFD framework-based study is carried out. Firstly, the methodology is presented, including the problem statement, the mathematical formulation and the main variables leading to the transport dynamics, meshing and solution schemes, and the description of the numerical experiments run in this work. Subsequently, the obtained results are discussed assessing the impact of the chemical scalars features on the transport behaviour. Finally, some conclusions are presented. Furthermore, some appendix are referenced.

## 2. Methodology
This study is addressed under a CFD approach, enabling to evaluate transport and retention phenomena at the pore-scale considering a continuous medium in the pore space. The followed methodology is presented below:

### Problem Statement

Aiming to simplify the problem, but keeping in mind the objectives of this study, a 2D geometry is generated. This geometry contains a regular porous medium in the middle formed by circular grains as shown in Figure 1. A fluid with a dispersed chemical scalar is injected into the domain at the inlet port, follows some transport dynamics, and exits at the outlet port. Inside the porous medium, the chemical scalars trend to be transported by the fluid flow. This mechanism corresponds to *advection*. In addition, concentration gradients in the medium lead to a scalar transport towards the regions with less concentration by *molecular diffusion*.

Transversaly, when the chemical scalars reach the porous medium, surface-level interactions generate a mass scalar flux from or towards the rock surface. The rate and the direction of this flux depends on the solid surface composition, chemical nature of the specie, chemical and dynamic properties of the carrier fluids, and concentrations in the fluid and retained onto the surface.

<figure>
  <img src="./Figures/General/geometry.jpeg" alt="geometry" style="width: 10px">
  <img src="./Figures/General/boundaries.jpeg" alt="geometry" style="width: 10px">
  <figcaption>Fig.1 - 2D Geometry used in this CFD study. All dimensions are in meters.</figcaption>
</figure>

Some assumptions are listed below:

<ul>
  <li>The carrier fluid behaves as a Newtonian fluid (i.e. viscosity is not a function of the shear rate).</li> 
  <li>The concentration of the chemical scalar does not affect fluid viscosity.</li>
  <li>There is no energy transport mechanism affecting the mass and momentum transports.</li>
</ul>

### Mathematical Formulation and Dimensionless Variables

As mentioned above, the transport of a scalar depends strongly on fluid flow in the porous medium. For this reason, this formulation is divided into two problems: the first one is based on the fluid flow through the porous media; meanwhile the second one is associated with the chemical scalar transport.

#### Incompressible flow

The widely known Navier-Stokes equations are used to model the fluid flow through the porous medium. By this approach, steady flow is considered, so the transient term is neglected. For a 2D problem, this is formed by 3 equations: one for fluid continuity and two for fluid momentum balance (one per dimension). By these equations, pressure and velocity distributions can be estimated for the spatial domain.

<img src="https://render.githubusercontent.com/render/math?math=\Large {\frac{\partial u_x}{\partial x}}%2B{\frac{\partial u_y}{\partial y}}=0">

<img src="https://render.githubusercontent.com/render/math?math=\Large u_x \frac{\partial u_x}{\partial x}%2B u_y \frac{\partial u_x}{\partial y}-\nu \left( \frac{\partial^2 u_x}{\partial x^2} %2B \frac{\partial^2 u_x}{\partial y^2} \right) %2B \frac{1}{\rho} \frac{\partial P}{\partial x}=0">

<img src="https://render.githubusercontent.com/render/math?math=\Large u_x \frac{\partial u_y}{\partial x}%2B u_y \frac{\partial u_y}{\partial y}-\nu \left( \frac{\partial^2 u_y}{\partial x^2}%2B \frac{\partial^2 u_y}{\partial y^2} \right) %2B \frac{1}{\rho} \frac{\partial P}{\partial y}=0">

In order to delimite the mathematical problem regarding incompressible flow, initial and boundary conditions are proposed based on the problem statement. As an initial condition, zero velocity and a constant pressure are considered.

<img src="https://render.githubusercontent.com/render/math?math=\Large u_x (t=0)=0, u_y (t=0)=0, P (t=0)=P_{out}">

Regarding the boundary conditions, constant velocity and pressure zero grandient are considered as inlet boundary conditions.

<img src="https://render.githubusercontent.com/render/math?math=\Large \frac{\partial P}{\partial x} |_{\small \textrm{inlet}}=0, u_x|_{\small \textrm{inlet}}=u_{in}, u_y|_{\small \textrm{inlet}}=0">

Although, at the outlet boundary, constant pressure and velocity zero gradient, corresponding to an outlow-type condition. 

<img src="https://render.githubusercontent.com/render/math?math=\Large P|_{\small \textrm{outlet}}=P_{out}, \frac{\partial u_x}{\partial x}|_{\small \textrm{outlet}}=0, \frac{\partial u_y}{\partial x}|_{\small \textrm{outlet}}=0">

For the grains boundary, a non-slip condition is considered. In this condition, fluid velocity and pressure gradient are set as zero. 

<img src="https://render.githubusercontent.com/render/math?math=\Large \frac{\partial P}{\partial x}|_{\small \textrm{grain}}=0, u_x|_{\small \textrm{grain}}=0, u_y|_{\small \textrm{grain}}=0">

Finally, upper and lower boundaries are considered as axes of symmetry. So, pressure, velocity, and their corresponding gradients are equal at the same distance from the planes.

Based on this mathematical model, two dimensionless numbers govern incompressible flow in the porous medium. Reybolds number is the ratio between intertial and viscous forces; meanwhile Ruark number corresponds to the ratio betweeen inertial and pressure forces.

<table>
  <caption style="text-align:right">Tab 1. Dimensionless numbers for incompressible flow problem.</caption>
  <tr>
    <th>Dimensionless</th>
    <th>Definition</th>
    <th>Description</th>
  </tr>
  <tr>
    <td><img src="https://render.githubusercontent.com/render/math?math=\Large N_{Re}"></td>
    <td><img src="https://render.githubusercontent.com/render/math?math=\Large \frac{v_c l_c}{\nu_c}"></td>
    <td>Reynolds Number</td>
  </tr>
    <tr>
    <td><img src="https://render.githubusercontent.com/render/math?math=\Large N_{Ru}"></td>
    <td><img src="https://render.githubusercontent.com/render/math?math=\Large \frac{\rho_c v_c^2}{\Delta P_c}"></td>
    <td>Ruark Number</td>
  </tr>
</table>
<br>

#### Chemical scalar transport
On the other hand, chemical scalar transport are modelled by the unsteady Advection-Diffusion (ADR) equation. By this equation, and with a predefined velocity field, the concentration field can be computed:

<img src="https://render.githubusercontent.com/render/math?math=\Large \frac{\partial c}{\partial t}-\left(u_x \frac{\partial c}{\partial x} %2B u_y \frac{\partial c}{\partial x} \right) %2B D \left( \frac{\partial^2 c}{\partial x^2} %2B \frac{\partial^2 c}{\partial y^2}\right)=0">

Following the same steps for the problem delimitation, a constant concentration field is considered as an initial condition of this problem:

<img src="https://render.githubusercontent.com/render/math?math=\Large c(t=0)=c_0">

As a boundary condition at inlet, a constant concentration is assumed:

<img src="https://render.githubusercontent.com/render/math?math=\Large c|_{\small \textrm{inlet}}=c_{in}">

Althought, a zero concentration gradient at the outlet is considered:

<img src="https://render.githubusercontent.com/render/math?math=\Large \frac{\partial c}{\partial x}|_{\small \textrm{outlet}}=0">

For the grains boundary, a model for retention is used to represent the surface phenomena. **Bueno et. al. (2020)** propose an schema based on an Langmuir-type retention model, in which attachment onto the surface depends on the chemical scalar concentration in the fluid and the retained concentration. So, this boundary condition can be expressed as follow:

<img src="https://render.githubusercontent.com/render/math?math=\Large -D\left( \frac{\partial^2 c}{\partial x^2} %2B \frac{\partial^2 c}{\partial y^2}\right) |_{\small \textrm{grain}} = K_a \left( 1-\frac{s}{s_{max}} \right)c - K_d s">

Finally, as it was assumed for the incompresssible flow problem, upper and lower boundaries are considered as axes of symmetry for concentration too.

For the chemical scalar transport, there are three dimensionless numbers characterising the problem. Péclet number corresponds to the ratio between advection and diffusion fluxes; meanwhile both Damkhöler numbers are defined as ratios between attachment/detachment and diffusion fluxes.

<table>
  <caption style="text-align:right">Dimensionless numbers for scalar transport problem.</caption>
  <tr>
    <th>Dimensionless</th>
    <th>Definition</th>
    <th>Description</th>
  </tr>
  <tr>
    <td><img src="https://render.githubusercontent.com/render/math?math=\Large N_{Pe}"></td>
    <td><img src="https://render.githubusercontent.com/render/math?math=\Large \frac{u_{in}L}{D}"></td>
    <td>Péclet Number</td>
  </tr>
    <tr>
    <td><img src="https://render.githubusercontent.com/render/math?math=\Large N_{Da,a}"></td>
    <td><img src="https://render.githubusercontent.com/render/math?math=\Large \frac{K_aL^2}{D}"></td>
    <td>Damkhöler Number (Attachment) </td>
  </tr>
  <tr>
    <td><img src="https://render.githubusercontent.com/render/math?math=\Large N_{Da,d}"></td>
    <td><img src="https://render.githubusercontent.com/render/math?math=\Large \frac{K_dL^2}{D}"></td>
    <td>Damkhöler Number (Detachment) </td>
  </tr>
</table>
<br>


### Meshing and solution schemes

To solve numerically the problem, a quad-based mesh is generated using the ANSYS ICEM CFD software, as shown in Figure 2. This mesh is refined in the most conflictive regions to guarantee a proper set of mesh quality indicators. 

<figure>
  <img src="./Figures/General/quadmesh.jpeg" alt="geometry" style="width: 10px">
  <figcaption>Fig.2- 2D Geometry used in this CFD study. All dimensions are in meters.</figcaption>
</figure>


Table 3 shows the features of the generated mesh.

<table>
  <caption style="text-align:right">Table 3. Mesh features.</caption>
  <tr>
    <th>Dimensions of grid</th>
    <th>Number of points</th>
    <th>Number of cells</th>
    <th>Number of faces</th>
  </tr>
  <tr>
    <td>2</td>
    <td>245 093</td>
    <td>238 806</td>
    <td>483 957</td>
  </tr>
</table>
<br>

Both problems, the incompressible flow and scalar transport ones, are solved using OpenFOAM, a widely recognised open source package for CFD applications. The mathematical model is discretised by the Finite Volume Method (FVM). In particular, the incompressible flow problem is solved using the simpleFoam solver, which follows the SIMPLE algorithm to estimate the velocity and pressure fields in the spatial domain. Meanwhile, the in-house version of the scalarTransportFoam solver, developed by the Multiscale Modelling and Heterogeneous Media group of the University of Nottingham, is used to solve the chemical scalar transport problem (**Bueno et. al. 2020**). This version includes the Langmuir-based kinetic to model the chemical scalar retention onto the rock surface.

### Experimental Design

<table>
  <caption style="text-align:right">Table 3. Mesh features.</caption>
  <tr>
    <th>Reynolds Number</th>
    <th>Nuarkk Number</th>
  </tr>
  <tr>
    <td>1e-3</td>
    <td>1e-3</td>
  </tr>
</table>
<br>



## 3. Results and Discussion

### Transport Problem

#### Effect of the size of the chemical scalar on the transport dynamics

### Effect of the size of the chemical scalar on the retention capacity

### Effect of the attachment rate

### Effect of the detachment rate

## 4. Conclusions

## 5. References


## Appendix A. Mesh independence study

## Appendix B. Model Validation

## Appendix C. Convergence Evaluation

## Appendix D. 
