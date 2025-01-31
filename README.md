# Transport Dynamics of Chemical Species in Porous Media: a 2D CFD study at the pore-scale
Hillmert A. Solano

## 1. Introduction
The injection of tailored solutions with chemical species, such as polymers, surfactants, nanoparticles, salts, and others; has become very common in subsurface engineering applications. Enhanced Oil Recovery (EOR) operations are a good example of these applications, in which chemical species are used to generate or favour different interactions that improve oil and gas production from hydrocarbons reservoirs. On another vein, the remotion of non-aqueous liquid phases (NAPL) and solid pollutants from soil and groundwater bodies can be improved using chemical species. Furthermore, recent studies show a positive impact on the carbon dioxide storage capacity when a Geological Carbon Sequestration (GCS) operation is upgraded using chemical species. All the above accounts for the importance of the study of chemical species behaviour in porous media targeting to improving its understanding and the design process of these operations.

One of the most important issues involved in the behaviour of chemical species in porous media are the transport phenomena. When a chemical species is injected into a porous medium, several transport mechanisms are followed (**Bear, 2018**). These mechanisms are strongly associated with its interactions with other species particles/molecules, the carrier fluid, and the solid surface (**Derjaguin and Landau, 2018**); and govern its deployment inside the porous medium. With this in mind, a proper representation of the chemical species transport dynamics inside the porous media is key to design a subsurface engineering application involving chemical species.

This work is focused on the phenomenological study of transport dynamics followed by chemical species in porous media. In order to address this objective, a CFD framework-based study is carried out. Firstly, the methodology is presented, including the problem statement, the mathematical formulation and the main variables leading to the transport dynamics, meshing and solution schemes. Subsequently, a set of numerical experiments are run, and the obtained results are discussed assessing the impact of the chemical species features on the transport behaviour. Finally, some conclusions are presented. Furthermore, some annexes with more detailed information regarding the CFD approach are referenced. The main interest of this work is to give a set of relevant key points to be taken into account for the design of engineering applications involving chemical species in subsurface.

## 2. Methodology
In this section, the methodology is proposed. Under a CFD approach, this study follows a phenomenological methodology (**Bear, 2018**) that is presented below.

### Problem Statement

Aiming to simplify the problem, but keeping in mind the objectives of this study, a 2D geometry is proposed. This geometry contains a regular porous medium formed by circular grains as shown in Figure 1. The study is delimited to the injection of a dispersed mass of chemical species in a single-phase fluid through the inlet port. This species is transported inside the spatial domain and exits at the outlet port. Inside the porous medium, the chemical species follows the carrier fluid flow by the advection mechanism (**Bear, 2018**). In addition, concentration gradients in the medium lead to a species transport towards the regions with less concentration by molecular diffusion (**Bear, 2018**).

Transversally, when the chemical species reach the porous medium, surface-level interactions generate a mass flux from or towards the rock surface (**Bueno et. al., 2019**, **Boccardo et. al., 2017**). The rate and the direction of this flux depends on the solid surface composition, chemical nature of the specie, properties of the carrier fluids respect to its chemical and dynamic behaviour, and species concentrations in the fluid and retained onto the surface.

<figure>
    <table border="0">
  <tr>
    <th><img src="./Figures/General/geometry.jpeg" alt="geometry" width="500px"></th>
</tr>
  <tr>
    <th><img src="./Figures/General/boundarycond.png" alt="geometry" width="500px"></th>
</tr>
</table>  
  <figcaption>Fig.1 - 2D Geometry used in this CFD study. At the left, the dimensions of the physical domain in meters. At the right, the definition of the boundaries and two axes used in the study.</figcaption>
  <br><br>
</figure>

Some assumptions are listed below:

<ul>
  <li>The carrier fluid behaves as a Newtonian fluid (i.e. viscosity is not a function of the shear rate).</li>
  <li>Flow regime is laminar (low Reynolds numbers).</li>
  <li>The concentration of the chemical species does not affect fluid viscosity (low concentration).</li>
  <li>The concentration of the chemical species does not affect diffusivity (Fickian mass transport).</li>
  <li>Diffusion coefficient is constant for all points in the space and all directions.</li>
  <li>Retention dynamics are irreversible. Retained species do not back to the fluid flow.</li>
  <li>There is no energy transport mechanism affecting the mass and momentum transports.</li>
</ul>

### Mathematical Formulation and Dimensionless Variables

As mentioned above, the transport of a species depends strongly on fluid flow in the porous medium. For this reason, this formulation is divided into two problems: the first one is based on the fluid flow through the porous media; meanwhile the second one is associated with the chemical species transport. For each case, a set of equations, and initial and boundary conditions are defined.

#### Incompressible flow

The widely known Navier-Stokes equations are used to model the fluid flow through the porous medium. By this approach, steady flow is considered, so the cumulation term is neglected. For a 2D problem, this is formed by 3 equations: one for fluid continuity and two for fluid momentum balance (one per dimension). By these equations, pressure and velocity distributions can be estimated for the spatial domain.

<img src="https://render.githubusercontent.com/render/math?math=\Large {\frac{\partial u_x}{\partial x}}%2B{\frac{\partial u_y}{\partial y}}=0">

<img src="https://render.githubusercontent.com/render/math?math=\Large u_x \frac{\partial u_x}{\partial x}%2B u_y \frac{\partial u_x}{\partial y}-\nu \left( \frac{\partial^2 u_x}{\partial x^2} %2B \frac{\partial^2 u_x}{\partial y^2} \right) %2B \frac{1}{\rho} \frac{\partial P}{\partial x}=0">

<img src="https://render.githubusercontent.com/render/math?math=\Large u_x \frac{\partial u_y}{\partial x}%2B u_y \frac{\partial u_y}{\partial y}-\nu \left( \frac{\partial^2 u_y}{\partial x^2}%2B \frac{\partial^2 u_y}{\partial y^2} \right) %2B \frac{1}{\rho} \frac{\partial P}{\partial y}=0">

where <img src="https://render.githubusercontent.com/render/math?math=\normalsize u_j"> is the j-component of the flow velocity vector, <img src="https://render.githubusercontent.com/render/math?math=\normalsize \nu"> is the kinematic viscosity of the fluid, <img src="https://render.githubusercontent.com/render/math?math=\normalsize \rho"> is the fluid density, and <img src="https://render.githubusercontent.com/render/math?math=\normalsize P"> is the pressure.

In order to delimite the mathematical problem, initial and boundary conditions are proposed based on the problem statement. As an initial condition, zero velocity and a constant pressure are considered.

<img src="https://render.githubusercontent.com/render/math?math=\Large u_x (t=0)=0, u_y (t=0)=0, P (t=0)=P_{out}">

where <img src="https://render.githubusercontent.com/render/math?math=\normalsize P_{out}"> is the initial pressure considered for the experiments. 

Regarding the boundary conditions, a fixed inlet-velocity and pressure zero gradient are considered as inlet boundary conditions.

<img src="https://render.githubusercontent.com/render/math?math=\Large \frac{\partial P}{\partial x} |_{\small \textrm{inlet}}=0, u_x|_{\small \textrm{inlet}}=u_{in}, u_y|_{\small \textrm{inlet}}=0">

where <img src="https://render.githubusercontent.com/render/math?math=\normalsize u_{in}"> is the injection velocity at the inlet port. 

Instead, at the outlet boundary, constant pressure and velocity zero gradient, corresponding to an outflow-type condition. 

<img src="https://render.githubusercontent.com/render/math?math=\Large P|_{\small \textrm{outlet}}=P_{out}, \frac{\partial u_x}{\partial x}|_{\small \textrm{outlet}}=0, \frac{\partial u_y}{\partial x}|_{\small \textrm{outlet}}=0">

For the grain's boundary, a non-slip condition is considered. In this condition, fluid velocity and pressure gradient are set as zero. 

<img src="https://render.githubusercontent.com/render/math?math=\Large \frac{\partial P}{\partial x}|_{\small \textrm{grain}}=0, u_x|_{\small \textrm{grain}}=0, u_y|_{\small \textrm{grain}}=0">

Finally, upper and lower boundaries are considered as axes of symmetry. So, pressure, velocity, and their corresponding gradients are equal at the same distance from the planes.

According to a dimensional analysis, two dimensionless numbers govern incompressible flow in the porous medium: Reynolds number and Ruark Number (known as well as the inverse Euler number). Reynolds number is the ratio between inertial and viscous forces; meanwhile Ruark number corresponds to the ratio between inertial and pressure forces. Other dimensionless numbers commonly obtained from the Navier-Stokes equations, like Froude and Darcy numbers, are neglected because gravitational component and fluid compressibility are not considered in this study.

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

#### Chemical species transport
On the other hand, chemical species transport is modelled by the unsteady Advection-Diffusion (ADR) equation. This equation represents the transport of a scalar in a spatial domain. In this case, the scalar is the concentration of the chemical species in the fluid. By this equation, and with a predefined velocity field, the concentration field can be computed:

<img src="https://render.githubusercontent.com/render/math?math=\Large \frac{\partial c}{\partial t}-\left(u_x \frac{\partial c}{\partial x} %2B u_y \frac{\partial c}{\partial x} \right) %2B D \left( \frac{\partial^2 c}{\partial x^2} %2B \frac{\partial^2 c}{\partial y^2}\right)=0">

where <img src="https://render.githubusercontent.com/render/math?math=\normalsize c"> is the species concentration in the fluid and <img src="https://render.githubusercontent.com/render/math?math=\normalsize D"> is the mass diffusion coefficient of the species in the fluid.

Considering that reactions are neglected, and Reynold number is low; the approximation proposed by Stokes-Einstein can be used to estimate the mass diffusion coefficient.

<img src="https://render.githubusercontent.com/render/math?math=\Large D = \frac{k_b T}{3 \pi \nu \rho d_s} ">


where <img src="https://render.githubusercontent.com/render/math?math=\normalsize k_b"> is the Boltzman constant (1.38e-23 J/K) and <img src="https://render.githubusercontent.com/render/math?math=\normalsize d_s"> is the diameter of the specie.

Following the same steps for the problem delimitation, a constant concentration field is considered as an initial condition of this problem:

<img src="https://render.githubusercontent.com/render/math?math=\Large c(t=0)=c_0">

where <img src="https://render.githubusercontent.com/render/math?math=\normalsize c_0"> is the initial concentration along the spatial domain. 

As a boundary condition at inlet, a fixed concentration is assumed:

<img src="https://render.githubusercontent.com/render/math?math=\Large c|_{\small \textrm{inlet}}=c_{in}">

where <img src="https://render.githubusercontent.com/render/math?math=\normalsize c_{in}"> is the concentration at the injection port.

In addition, a zero-concentration gradient at the outlet is considered:
 
<img src="https://render.githubusercontent.com/render/math?math=\Large \frac{\partial c}{\partial x}|_{\small \textrm{outlet}}=0">

For the grain’s boundary, a model for retention is used to represent surface phenomena. **Bueno et. al. (2020)** propose a schema based on a Langmuir-type retention model, in which attachment onto the surface depends on the chemical species concentration in the fluid and the retained concentration. So, this boundary condition can be expressed, for an irreversible dynamic, as follow:

<img src="https://render.githubusercontent.com/render/math?math=\Large -D\left( \frac{\partial^2 c}{\partial x^2} %2B \frac{\partial^2 c}{\partial y^2}\right) |_{\small \textrm{grain}} = K_a \left( 1-\frac{s}{s_{max}} \right)c">

where <img src="https://render.githubusercontent.com/render/math?math=\normalsize s"> is the retained concentration onto the solid surface, 
where <img src="https://render.githubusercontent.com/render/math?math=\normalsize s_{max}"> is the solid surface capacity, and
where <img src="https://render.githubusercontent.com/render/math?math=\normalsize k_a"> is the kinetic constants representing attachment rate of the species onto/from the rock surface.

Meanwhile, solid surface capacity can be estimated based on a surface occupancy by the next equation:

<img src="https://render.githubusercontent.com/render/math?math=\Large s_{max} = \frac{\pi}{6}  a_s \rho_s d_s ">

where <img src="https://render.githubusercontent.com/render/math?math=\normalsize d_s" > is the diameter of the specie,  <img src="https://render.githubusercontent.com/render/math?math=\normalsize a_s"> is the surface area to porous volume ratio, and <img src="https://render.githubusercontent.com/render/math?math=\normalsize \rho_s"> is the specie density.

Finally, as it is assumed for the incompresssible flow problem, upper and lower boundaries are considered as axes of symmetry for concentration too.

For the chemical species transport, there are two dimensionless numbers characterising the problem. Péclet number corresponds to the ratio between advection and diffusion fluxes; meanwhile both Damkhöler number are defined as ratios between attachment and diffusion fluxes.

<table>
  <caption style="text-align:right">Dimensionless numbers for species transport problem.</caption>
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
    <td>Damkhöler Number </td>
  </tr>
</table>
<br>


### Meshing

To solve numerically the problem, a quad-based mesh is generated using the ANSYS ICEM CFD software (**ANSYS, 2020**), which is shown in Figure 2. This mesh is refined in the most conflictive regions to guarantee a proper set of mesh quality indicators. Table 3 shows the features of the generated mesh.

<figure>
  <img src="./Figures/General/quadmesh.jpeg" alt="geometry" style="width: 10px">
  <figcaption>Fig.2- 2D Geometry used in this CFD study. All dimensions are in meters.</figcaption>
</figure>
<br><br>

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

A mesh independence assessment is presented in the Annex 1. 

### Solution schemes

To solve the mathematical formulation, both problems are solved separately. This is possible due to the time required to reach the steady state in the incompressible flow is enough low respect to the species transport if the Reynolds and Ruark numbers are typical values used for geological porous media (**Bueno et. al., 2020**). Both problems, the incompressible flow and species transport ones, are solved using OpenFOAM (**OpenFOAM, 2018a, 2018b**), a widely recognised open source package for CFD applications with a Finite Volume-based framework (**Moukalled, 2016**).

#### Incompressible Flow

The incompressible flow problem is solved using the simpleFoam solver (**OpenFOAM, 2018a**), which follows the Semi-Implicit Method for Pressure Linked Equations (SIMPLE) algorithm to estimate the velocity and pressure fields in the spatial domain (**Caretto, 1973**). This algorithm shows a better performance with respect to the other ones available in OpenFOAM at the conditions of the experiments. The above is concluded from a convergence study presented in the Annex 2. The numerical solution schemes for this problem are presented below in Table 3.

<table>
  <caption style="text-align:right">Table 3. Numerical solution features for the incompressible flow problem.</caption>
  <tr>
    <th>Feature</th>
    <th>Scheme</th>
  </tr>
  <tr>
    <td>Transient term Scheme</td>
    <td>Steady State</td>
  </tr>  
  <tr>
    <td>Gradient Scheme</td>
    <td>Gauss linear</td>
  </tr>  
  <tr>
    <td>Divergence Scheme</td>
    <td>Bounded Gauss Linear Upwind for velocity gradient</td>
  </tr>  
  <tr>
    <td>Laplacian Scheme</td>
    <td>Gauss linear corrected</td>
  </tr>
  <tr>
    <td>Linear solver por velocity</td>
    <td>Smooth solver with Gauss-Seidel smoother</td>
  </tr>
  <tr>
    <td>Linear solver por pressure</td>
    <td>GAMG with Gauss-Seidel smoother</td>
  </tr>
</table>
<br>


#### Species Transport

The chemical specie transport problem is solved using the scalarTransportFoam solver (**OpenFOAM, 2018b**). Particularly, the adaptation developed by the ***Multiscale Modelling and Heterogeneous Media group*** of the University of Nottingham is used because it includes a proper boundary condition representation for the retention dynamics onto solid surfaces based on Langmuir kinetic and others (**Bueno et. al. 2020**). **Bueno et. al. 2020** show a more detailed information respect to the implementation of this computational model.

The numerical solution schemes for this problem are presented below in Table 4.

<table>
  <caption style="text-align:right">Table 4. Numerical solution features for the species transport problem.</caption>
  <tr>
    <th>Feature</th>
    <th>Scheme</th>
  </tr>
  <tr>
    <td>Transient term Scheme</td>
    <td>Euler</td>
  </tr>  
  <tr>
    <td>Gradient Scheme</td>
    <td>Gauss linear</td>
  </tr>  
  <tr>
    <td>Divergence Scheme</td>
    <td>Bounded Gauss Linear Upwind for velocity gradient</td>
  </tr>  
  <tr>
    <td>Laplacian Scheme</td>
    <td>Gauss linear corrected</td>
  </tr>
  <tr>
    <td>Linear solver</td>
    <td>PBiCGStab with DILU precondicioner</td>
  </tr>
</table>
<br>

## 3. Experiments and Results

In this section, the experimental set is proposed and run. For the incompressible flow problem, one (1) experiment is proposed. Based on the outcomes generated by this one, seven (7) experiments for the species transport problem are run.

### Incompressible flow

The incompressible flow simulation is run using the input data presented in Table 5. This table contains the dimensionless numbers obtained from the input variables.

<table>
  <caption style="text-align:right">Table 5. Input data used for the incompressible flow simulation.</caption>
  <tr>
    <th><img src="https://render.githubusercontent.com/render/math?math=\normalsize u_{in}"> (m/s) </th>
    <th><img src="https://render.githubusercontent.com/render/math?math=\normalsize P_{out}"> (Pa) </th>
    <th><img src="https://render.githubusercontent.com/render/math?math=\normalsize \nu"> (<img src="https://render.githubusercontent.com/render/math?math=\normalsize m^2/s">)</th>
    <th><img src="https://render.githubusercontent.com/render/math?math=\normalsize \rho"> (<img src="https://render.githubusercontent.com/render/math?math=\normalsize kg/m^3">)</th>
    <th><img src="https://render.githubusercontent.com/render/math?math=\normalsize \Delta P_c"> (Pa)</th>
    <th><img src="https://render.githubusercontent.com/render/math?math=\normalsize N_{Re}"> </th>
    <th><img src="https://render.githubusercontent.com/render/math?math=\normalsize N_{Ru}"> </th>
</tr>
  <tr>
    <td>3.53e-06</td>
    <td>0.00e+00</td>
    <td>1.00e-06 </td>
    <td>1.00e+03 </td>
    <td>9.60e-05 </td>
    <td>4.92e-03 </td>
    <td>1.30e-04 </td>
  </tr>
</table>

From this CFD simulation, velocity and pressure fields are obtained. Figure 3 shows the pressure heatmap obtained by simulation. This plot shows that pressure drop between the inlet port and the outlet port is caused mainly by the flow dynamics in the porous media, which is expected considering the Darcy's law. It is expected that the magnitude of the pressure drop is a function of the fixed inlet-velocity.

<figure>
  <table border="0">
  <tr>
    <th><img src="./Figures/Incompressible%20Flow/pressurefield.jpeg" alt="geometry" height="300px"> </th>
</tr>
</table>
  <figcaption>Fig.3- Pressure field obtained from the incompressible flow simulation.</figcaption> <br><br>
</figure>


On another vein, Figure 4 shows the velocity magnitude heatmap with a set of streamlines obtained by postprocessing; while Figure 5 contains two velocity magnitude profiles along a vertical and an horizontal axes located at x=0.0009m and y=0.0007m respectively (see Figure 1). Both figures show that there are local gradients of velocity magnitude in the pore throats. These gradients can be explained by momentum transfers due to viscous forces between two non-slipping walls in each throat, in which the maximum velocity is reached at the middle point of the pore throat and a zero-relative velocity at the walls.

Furthermore, the plotted streamlines show a preferential trend in following the direction of the pressure gradient. Comparing with velocity heatmap, a reasonable conclusion is that the higher velocity magnitudes correspond to the zones with greater streamlines densities. For this reason, high-velocity zones lead to preferential flow paths in the porous medium.

<figure>
  <table border="0">
  <tr>
    <th><img src="./Figures/Incompressible%20Flow/velocityfield.jpeg" alt="geometry" height="300px"> </th>
    <th><img src="./Figures/Incompressible%20Flow/velocityfieldzoomed.jpeg" alt="geometry" height="300px"></th>
</tr>
</table>
  <figcaption>Fig.4- Velocity field obtained from the incompressible flow simulation. Left: whole image, right: zoomed. In the pictures, some streamlines are plotted. </figcaption><br><br>
</figure>


<figure>
  <table border="0">
  <tr>
    <th><img src=".//Figures/Incompressible%20Flow/velocitytransversal.jpeg" alt="geometry" height="500px"> </th>
    <th><img src=".//Figures/Incompressible%20Flow/velocitylong.jpeg" alt="geometry" height="500px"> </th>
</tr>
</table>
  <figcaption>Fig.5-  Cartesian plots of velocity vs. distance along two different axes. Left: x=0.0009m (vertical), right: y=0.0007 (horizontal).</figcaption><br><br>
</figure>


From the above, the outcomes obtained from the incompressible flow simulation are consistents and can be applied to run the species transport simulations.

### Species Transport

In order to address this study, a set of seven numerical experiments was run. The corresponding dataset is presented in Table 6. Experiment 1 simulates a hypothetical case where transport mechanisms by diffusion and retention dynamics are neglected, so the advection governs the chemical species transport across the porous medium. Instead, Experiments 2, 3, and 4 corresponds to cases for a specific chemical species size neglecting retention dynamics. Finally, Experiments 5, 6, and 7 simulate the same cases of the three last ones considering a constant retention rate. 
  
<table>
  <caption style="text-align:right">Table 6. Input data used for the numerical experiments.</caption>
  <tr>
    <th>ID</th>
    <th>Diameter (nm) </th>
    <th><img src="https://render.githubusercontent.com/render/math?math=\large k_a"> (1/s) </th>
    <th>D (<img src="https://render.githubusercontent.com/render/math?math=\normalsize m^2/s">) </th>
    <th><img src="https://render.githubusercontent.com/render/math?math=\large s_{max}"> (<img src="https://render.githubusercontent.com/render/math?math=\normalsize kg/m^3">)</th>
    <th><img src="https://render.githubusercontent.com/render/math?math=\Large N_{Pe}"> </th>
    <th><img src="https://render.githubusercontent.com/render/math?math=\Large N_{Da,a}"> </th>
    <th>Animation </th>
    <th>Animation (zoomed) </th>
</tr>
  <tr>
    <td> 1</td>
    <td>- </td>
    <td>0.00e+00 </td>
    <td>0.00e+00 </td>
    <td>- </td>
    <td>- </td>
    <td>0.00e+00 </td>
    <td><p><a href="https://www.youtube.com/watch?v=UbzHim_1x0U">Video</a></p> </td>
    <td><p><a href="https://www.youtube.com/watch?v=TBKmxifALT0">Video</a></p> </td>
  </tr>
  <tr>
    <td> 2</td>
    <td>10 </td>
    <td>0.00e+00 </td>
    <td>4.32e-11 </td>
    <td>3.67e-01 </td>
    <td>20.53 </td>
    <td>0.00e+00 </td>
    <td><p><a href="https://www.youtube.com/watch?v=tC7wnuEwXq8">Video</a></p> </td>
    <td><p><a href="https://www.youtube.com/watch?v=EtOTb5CJTCc">Video</a></p> </td>
  </tr>
  <tr>
    <td> 3</td>
    <td> 50</td>
    <td>0.00e+00 </td>
    <td>8.64e-12 </td>
    <td>1.83e+00 </td>
    <td>102.65 </td>
    <td>0.00e+00 </td>
    <td><p><a href="https://www.youtube.com/watch?v=xm6KSwjxmQY">Video</a></p> </td>
    <td><p><a href="https://www.youtube.com/watch?v=TTHVxNuWjdI">Video</a></p> </td>
  </tr>
  <tr>
    <td>4</td>
    <td>100</td>
    <td>0.00e+00 </td>
    <td>4.32e-12 </td>
    <td>3.67e+00 </td>
    <td>205.30 </td>
    <td>0.00e+00 </td>
    <td><p><a href="https://www.youtube.com/watch?v=PmyAC1zPRU8">Video</a></p> </td>
    <td><p><a href="https://www.youtube.com/watch?v=EVIjJY_LxTg">Video</a></p> </td>
  </tr>
  <tr>
    <td>5</td>
    <td>10</td>
    <td>1.00e-07 </td>
    <td>4.32e-11 </td>
    <td>3.67e-01 </td>
    <td>20.53 </td>
    <td>1.46e-04 </td>
    <td><p><a href="https://www.youtube.com/watch?v=KaFeWjrQV3U">Video</a></p> </td>
    <td><p><a href="https://www.youtube.com/watch?v=vnQHHuDpRXo">Video</a></p> </td>
  </tr>
  <tr>
    <td>6</td>
    <td>50</td>
    <td>1.00e-07 </td>
    <td>8.64e-12 </td>
    <td>1.83e+00 </td>
    <td>102.65 </td>
    <td>7.31e-04 </td>
    <td><p><a href="https://www.youtube.com/watch?v=9jOkrxBxqAg">Video</a></p> </td>
    <td><p><a href="https://www.youtube.com/watch?v=jwDzBNLhNRY">Video</a></p> </td>
  </tr>
  <tr>
    <td>7</td>
    <td>100</td>
    <td>1.00e-07 </td>
    <td>4.32e-12 </td>
    <td>3.67e+00 </td>
    <td>205.30 </td>
    <td>1.46e-03 </td>
    <td><p><a href="https://www.youtube.com/watch?v=g_SVaWlDfDA">Video</a></p> </td>
    <td><p><a href="https://www.youtube.com/watch?v=rdLdOiCMbxo">Video</a></p> </td>
  </tr>
</table>
<br>

The next schedule is simulate for all of the proposed experiments:

<ul>
  <li> Injection of a fluid with a dispersed concentration of <img src="https://render.githubusercontent.com/render/math?math=\normalsize 1 kg/m^3"> between 0s to 1200s.
  <li> Injection of a fluid with a dispersed concentration of <img src="https://render.githubusercontent.com/render/math?math=\normalsize 0 kg/m^3"> between 1200s to 2400s.
</ul>
  
A time-step of 6s has been chosen for all simulations. Annex 3 presents a time-step independence analysis that concludes that this value is proper to this type of simulation.

### Effect of the diffusion on the chemical species transport

Figure 6 presents a set of screenshots obtained from the simulation video zoomed to pore scale for Experiments 1 and 3. These screenshots are obtained at t=480 s (during the dispersion injection), t=1200 s (when the dispersion injection stops), and t=1680 s (during fresh fluid injection) for both cases. 


<figure>
  <table border="0">
  <tr>
    <th><img src="./Experiments/Experiment1/animationzoom_experiment1_CDF-porousmedia_8min.jpg" alt="geometry" height="300px"> </th>
    <th><img src="./Experiments/Experiment1/animationzoom_experiment1_CDF-porousmedia_20min.jpg" alt="geometry" height="300px"> </th>
    <th><img src="./Experiments/Experiment1/animationzoom_experiment1_CDF-porousmedia_28min.jpg" alt="geometry" height="300px"> </th>
</tr>
  <tr>
    <th>Experiment 1. 480 s. </th>
    <th>Experiment 1. 1200 s. </th>
    <th>Experiment 1. 1680 s. </th>
</tr>
<tr>
    <th><img src="./Experiments/Experiment3/animationzoom_experiment3_CDF-porousmedia_8min.jpg" alt="geometry" height="300px"> </th>
    <th><img src="./Experiments/Experiment3/animationzoom_experiment3_CDF-porousmedia_12min.jpg" alt="geometry" height="300px"> </th>
    <th><img src="./Experiments/Experiment3/animationzoom_experiment3_CDF-porousmedia_28min.jpg" alt="geometry" height="300px"> </th>
</tr>
  <tr>
    <th>Experiment 3. 480 s. </th>
    <th>Experiment 3. 1200 s. </th>
    <th>Experiment 3. 1680 s. </th>
</tr>
</table>
  <figcaption>Fig.6-  Screenshots obtained from simulation corresponding to Experiment 1 (upper) and Experiment 3 (lower). For each experiment, the screeshots correspond to 480 s (left), 1200 s (centre), and 1680 s (right). </figcaption>
  <br> <br>
</figure>

In the upper plots, corresponding to the non-diffusion case, species trends to be transported mainly across the high streamlines’ density zones. Then, when these regions reach a species concentration equal to the injection one, the species begins to be transported toward low streamlines’ density zones reaching concentration greater than the injection ones. This particularity is associated with the low transport potential in these regions caused by the low flow potential, generating species cumulation in these places. In contrast, when diffusion is considered, the maximum concentration reached in the whole porous space corresponds to the injection one.  The presence of the mass diffusion mechanisms enables species transport towards the low streamlines’ density regions and avoids a cumulation in these regions. 

### Effect of the size of the chemical species in transport (without retention)

To evaluate the effect of the species size on the transport dynamics neglecting the effect of the retention, Experiments 2, 3, and 4 are compared. Figure 7 contains some heatmaps corresponding to these experiments at the moment before reaching the injection concentration at the exit port.

<figure>
  <table border="0">
  <tr>
    <th><img src="./Experiments/Experiment2/animation_experiment2_CDF-porousmedia_beforebt.jpg" alt="geometry" height="250px"> </th>
    <th><img src="./Experiments/Experiment3/animation_experiment3_CDF-porousmedia_beforebt.jpg" alt="geometry" height="250px"> </th>
    <th><img src="./Experiments/Experiment4/animation_experiment4_CDF-porousmedia_beforebt.jpg" alt="geometry" height="250px"> </th>
</tr>
  <tr>
    <th>Experiment 2. </th>
    <th>Experiment 3. </th>
    <th>Experiment 4. </th>
</tr>
</table>
  <figcaption>Fig.7-  Screenshot obtained from simulation corresponding to Experiment 2 (left), Experiment 3 (centre), and Experiment 4 (right) at the moment before reaching the injection concentration at the outlet port. </figcaption>
  <br> <br>
</figure>

From these plots, it can be noted that the concentration front is more homogeneous when the species size is lower because diffusive flux gets higher. Instead, when the species size is greater, the front trends to be transported mainly towards the streamlines' high-density regions. However, unlike the non-retention case, a higher concentration than the injection ones are not reached at no point in the spatial domain.

Figure 8 contains the breakthough curves for these experiments, which corresponds to concentration plot over time at the exit port for each one. 

<figure>
  <table border="0">
  <tr>
    <th><img src="./Figures/ScalarTranport/breakthrough-nonretention.png" alt="geometry" height="500px"> </th>
</tr>
</table>
  <figcaption>Fig.8-  Breakthrough curves obtained for Experiment 1,  2, 3, and 4. </figcaption>
  <br> <br>
</figure>

The above curves show a delay for the higher species size (i.e. lower diffusion coefficient) because the mass diffusion flux favours the transport towards the exit. However, the faster breakthrough corresponds to the non-diffusion case (i.e.  ). This is a consequence of the slow invasion of the chemical species in the regions with low transport potential, so the injected species is transported towards the outlet port.

### Effect of the size of the chemical species in transport (with retention)

To study the effect of the chemical species size on transport dynamics considering retention, Figure 9 contains the breakthrough curves for experiments 5, 6, and 7. 

<figure>
    <table border="0">
  <tr>
    <th><img src="./Figures/ScalarTranport/breakthrough-retention-diameter.png" alt="geometry" height="500px"> </th>
</tr>
</table> 
  <figcaption>Fig.9-  Breakthrough curves obtained for Experiment 5, 6, and 7. </figcaption>
  <br> <br>
</figure>

From these curves, it can be noted that the maximum concentration reached at the outlet port depends on the species size, reaching a greater concentration for a larger size. This is a consequence of the dependence of a higher rock surface capacity for species attachment, which reduces the retention and increases the species transport towards the outlet port.

### Effect of the retention in the transport

Aiming to evaluate the effect of the retention on transport dynamics, Figure 10 shows the evolution of concentration profile along the axis y=0.0007m (horizontal) for Experiment 3 (without retention) and Experiment 4 (with retention) for a species with size of 50nm.

<figure>
    <table border="0">
  <tr>
    <th><img src="./Experiments/Experiment3/graphs_prebreakthrough.png" alt="geometry" height="350px"> </th>
    <th><img src="./Experiments/Experiment6/graphs_prebreakthrough.png" alt="geometry" height="350px"> </th>
</tr>
<tr>
    <th>Without retention. </th>
    <th>With retention. </th>
</tr>
      </table>
  <figcaption>Fig.10-  Comparison between cases without and with retention for a species size of 50 nm. Each plot shows the evolution of the concentration profile along the horizontal axis at y=0.0007m. </figcaption>
  <br> <br>
</figure>

According to these plots, injection concentration is reached in all the spatial domain in the non-retention case while in the retention case the concentration reaches a concentration distribution. This difference can be explained by the retention dynamics where a part of the injected species mass is retained onto the rock surface while the rest is transported across the porous medium. Instead, where there is no retention, all species mass is transported in the porous medium by the defined mechanisms.

## 4. Conclusions

<ul>
  <li>A CFD-based approach enables the study of chemical species transport in porous media at the microscale. By this, it is possible to forecast the dynamic deployment of the chemical species according to its hydrodynamics and retention mechanisms. </li>
  <li>Incompressible flow in porous media is governed by mass and momentum transport. The distribution of the velocity field depends strongly on the porous medium morphology, being greater at the pore throats. </li>
  <li>Species transport depends on the velocity field. When the ratio between diffusion and advection fluxes trends to zero, the species are mainly transported following the streamlines.</li>
  <li>Chemical species retention onto the rock surface affects the transport dynamics inside the porous media. When there is a retention rate, a part of the injected scalar is retained in the porous medium and it is not recovered at the outlet port.</li>
  <li>The size of the chemical species is a key factor in its transport across the porous medium. First, it determines the diffusion coefficient, affecting the hydrodynamic of the process . In addition, it condiciones the rock surface capacity to be occupied by the species, being important to determine the evolution of the concentration field over time.   </li>
</ul>

## Annex 1: Mesh independence analysis

In this annex, a mesh independence analysis is addressed. In that sense, three grids are proposed for this objective and the results obtained by the incompressible flow simulation are compared. These grids are generated using the ANSYS ICEM CFD software, and its features are presented in Table 7. Meshes 1 and 3 are shown in Figure 11 while mesh 2, corresponding to the base one, is plotted in Figure 2. Mesh 1 is more refined mesh than the base one while Mesh 3 is coarser.

<table>
  <caption style="text-align:right">Table 7. Meshes features used for the mesh independence analysis.</caption>
  <tr>
    <th>ID</th>
    <th>Type</th>
    <th>Dimensions of grid</th>
    <th>Number of points</th>
    <th>Number of cells</th>
    <th>Number of faces</th>
  </tr>
  <tr>
    <td>1</td>
    <td>Tri</td>
    <td>2</td>
    <td>273 634</td>
    <td>534 702</td>
    <td>808 394</td>
  </tr>
  <tr>
    <td>2</td>
    <td>Quad</td>
    <td>2</td>
    <td>245 093</td>
    <td>238 806</td>
    <td>483 957</td>
  </tr>
  <tr>
    <td>3</td>
    <td>Tri</td>
    <td>2</td>
    <td>81 277</td>
    <td>156 207</td>
    <td>237 542</td>
  </tr>
</table>



<figure>
  <table border="0">
  <tr>
    <th><img src="./Figures/General/mesh1.jpeg" alt="geometry" height="500px"> </th>
    <th><img src="./Figures/General/mesh3.jpeg" alt="geometry" height="500px"> </th>
  </tr>
  </table>
  <figcaption> Fig.11- Additional meshes used to study the independence. Mesh 1 (left), Mesh 3 (right) </figcaption>
  <br> <br>
</figure>


Then, by running the corresponding incompressible flow simulations using the simpleFoam solver, it is possible to compare the outcomes. Figure 12 shows the velocity profile along a section of the vertical axis plotted in Figure 1-right by using three meshes.

<figure>
  <table border="0">
  <tr>
    <th><img src="./Figures/Incompressible%20Flow/comparison%20grids.png" alt="geometry" height="500px"> </th>
  </tr>
  </table>
  <figcaption> Fig.12- Residual logs obtained for different algorithms for incompressible flow solution.  Pressure (left), velocities (right). </figcaption>
  <br> <br>
</figure>

As a main conclusion, the proposed meshes can be used in this study. The maximum error at the maximum velocity magnitude, where the difference is greater, is around 2%. Hence, the mesh generating a lower run-time among these three is chosen. In this case, it is the mesh 2.


## Annex 2: Convergence Study

Aiming to select the best method to solve the numerical model regarding the incompressible flow problem in OpenFOAM. The available methods are Semi-Implicit Method for Pressure Linked Equations (SIMPLE), Pressure-Implicit with Splitting of Operators (PISO) in steady and unsteady flow, and the combination of both ones (PIMPLE). The next Figure contains the residual logs obtained for these simulations.

<figure>
  <table border="0">
  <tr>
    <th><img src="./Figures/Convergence/methodscomparisonp.jpg" alt="geometry" height="350px"> </th>
    <th><img src="./Figures/Convergence/methodscomparisonv.jpg" alt="geometry" height="350px"> </th>
  </tr>
  </table>
  <figcaption> Fig.13- Residual logs obtained for different algorithms for incompressible flow solution.  Pressure (left), velocities (right). </figcaption>
  <br> <br>
</figure>

This figure shows clearly that the solution by the SIMPLE algorithm shows a faster and more stable solution with respect to the other ones. In this sense, this is the more appropriate method to run the simulations.

## Annex 3: Timestep independence analysis

In order to select a proper timestep in the proposed CFD simulations, a previous evaluation of time step independence is carried out. Keeping this in mind, the proposed numerical experiment framework is run until 300 s for several timesteps. Then, the results are post-processed and a concentration profile over a horizontal axis (parallel to x-axis) is obtained for each considered timestep. These results are used to find the best timestep to run the simulations proposed in this project.

The timestep values used in this evaluation are presented below:

<table style="width:100%">
    <caption style="text-align:right">Table 8. Steps and timesteps used for the independence study.</caption>
  <tr>
    <th>Steps</th>
    <th>Timestep (s)</th>
    <th>Mean Courant</th>
    <th>Max. Courant</th>
  </tr>
    <td>1</td>
    <td>300</td>
    <td>575.96</td>
    <td>6073.88</td>
  </tr>
  <tr>
    <td>10</td>
    <td>30</td>
    <td>57.596</td>
    <td>607.388</td>
  </tr>
  <tr>
    <td>30</td>
    <td>10</td>
    <td>19.1987</td>
    <td>202.463</td>
  </tr>
  <tr>
    <td>50</td>
    <td>6</td>
    <td>11.5192</td>
    <td>121.478</td>
  </tr>
  <tr>
    <td>300</td>
    <td>1</td>
    <td>1.91987</td>
    <td>20.2463</td>
  </tr>
</table>

Then, the concentration profiles over the horizontal axis at y=0.007m is presented below:

<figure>
  <img src="./Figures/ScalarTranport/dtsensibility.png" alt="sensibility" width="700px">
  <figcaption>Fig.14- Concentration profile over a horizontal axis at y=0.0007m.</figcaption>
  <br>
<br>
</figure>

From the previous plot, different concentration profiles for this problem are obtained for several timestep values. However, when the timesteps increase, the corresponding profiles trend to a particular one. In this way, the concentration profiles for 6 seconds lower timesteps are equals. Hence, a timestep lower than **6 seconds** ensures timestep independence in this problem. This value is used for the CFD simulations.

Then, the residuals log for each timestep are presented below:

<figure>
  <img src="./Figures/ScalarTranport/dtsensibilityresidual.png" alt="sensibility2" width="700px">
  <figcaption>Fig.15- Residuals obtained from the simulations varying the timestep.</figcaption>
  <br>
<br>
</figure>

Even though a 1 second timestep enables lower residuals with respect to the 6 second one, the difference between both concentration profiles is lower. Therefore, the difference between both residuals does not affect the simulation output. 


## References

ANSYS (2020). ANSYS ICEN CFD Tutorial Manual. ANSYS, Inc.

Bear, J. (2018). Modeling phenomena of flow and transport in porous media (Vol. 1). Cham: Springer International Publishing.

Boccardo, G., Crevacore, E., Sethi, R., & Icardi, M. (2018). A robust upscaling of the effective particle deposition rate in porous media. Journal of contaminant hydrology, 212, 3-13.

Bueno, N., Icardi, M., Municchi, F., Solano, H., & Mejía, J. (2020, September). Upscaling of Nanoparticle Retention Rate for Single-Well Applications From Pore-Scale Simulations. In ECMOR XVII (Vol. 2020, No. 1, pp. 1-15). European Association of Geoscientists & Engineers.

Caretto, L. S., Gosman, A. D., Patankar, S. V., & Spalding, D. B. (1973). Two calculation procedures for steady, three-dimensional flows with recirculation. In Proceedings of the third international conference on numerical methods in fluid mechanics (pp. 60-68). Springer, Berlin, Heidelberg.

Derjaguin, B., & Landau, L. (1993). Theory of the stability of strongly charged lyophobic sols and of the adhesion of strongly charged particles in solutions of electrolytes. Progress in Surface Science, 43(1-4), 30-59.

Moukalled, F., Mangani, L., & Darwish, M. (2016). The finite volume method in computational fluid dynamics (Vol. 113, pp. 10-1007). Berlin, Germany:: Springer.

OpenFOAM (2018a). simpleFoam. In OpenFOAM User Guide. OpenFOAM Ltd. Available on www.openfoam.com/documentation/guides/latest/doc/guide-applications-solvers-incompressible-simpleFoam.html

OpenFOAM (2018b). scalarTransportFoam. In OpenFOAM User Guide. OpenFOAM Ltd. Available on www.openfoam.com/documentation/guides/latest/doc/guide-applications-solvers-incompressible-simpleFoam.html
