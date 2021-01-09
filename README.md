# Transport and retention of passive scalars in porous media: a CFD-based study at the pore-scale
Hillmert Solano, Faculty of Mines, Universidad Nacional de Colombia
## Presentation (video)

## Introduction


## Methodology
In order to address transport and retention dynamic of passive scalars in porous media at the pore-scale, a CFD framework is proposed. 

### Problem Statement

### Mathematical Formulation

#### Incompressible flow

<img src="https://render.githubusercontent.com/render/math?math=\Large {\frac{\partial u_x}{\partial x}}%2B{\frac{\partial u_y}{\partial y}}=0">

<img src="https://render.githubusercontent.com/render/math?math=\Large u_x \frac{\partial u_x}{\partial x}%2B u_y \frac{\partial u_x}{\partial y}-\nu \left( \frac{\partial^2 u_x}{\partial x^2} %2B \frac{\partial^2 u_x}{\partial y^2} \right) %2B \frac{1}{\rho} \frac{\partial P}{\partial x}=0">

<img src="https://render.githubusercontent.com/render/math?math=\Large u_x \frac{\partial u_y}{\partial x}%2B u_y \frac{\partial u_y}{\partial y}-\nu \left( \frac{\partial^2 u_y}{\partial x^2}%2B \frac{\partial^2 u_y}{\partial y^2} \right) %2B \frac{1}{\rho} \frac{\partial P}{\partial y}=0">

<img src="https://render.githubusercontent.com/render/math?math=\Large \frac{\partial P}{\partial x}=0, u_x=u_{in}, u_y=0">
<img src="https://render.githubusercontent.com/render/math?math=\Large P=P_{out}, \frac{\partial u_x}{\partial x}=0, \frac{\partial u_y}{\partial x}=0">
<img src="https://render.githubusercontent.com/render/math?math=\Large \frac{\partial P}{\partial x}=0, u_x=0, u_y=0">

#### Passive scalar transport

<img src="https://render.githubusercontent.com/render/math?math=\Large \frac{\partial c}{\partial t}-\left(u_x \frac{\partial c}{\partial x} %2B u_y \frac{\partial c}{\partial x} \right) %2B D \left( \frac{\partial^2 c}{\partial x^2} %2B \frac{\partial^2 c}{\partial y^2}\right)=0">

<img src="https://render.githubusercontent.com/render/math?math=\Large c=c_{in}">
<img src="https://render.githubusercontent.com/render/math?math=\Large \frac{\partial c}{\partial x}=0">
<img src="https://render.githubusercontent.com/render/math?math=\Large -D\left( \frac{\partial^2 c}{\partial x^2} %2B \frac{\partial^2 c}{\partial y^2}\right) = K_a \left( 1-\frac{s}{s_{max}} \right)c - K_d s">

### Dimensionless variables

| Dimensionless | Definition | Description |
| ------------- | ------------- | ------------- |
| <img src="https://render.githubusercontent.com/render/math?math=\Large N_{Pe}">  | <img src="https://render.githubusercontent.com/render/math?math=\Large \frac{u_{in}L}{D}">  | Contenido de la celda  |
| <img src="https://render.githubusercontent.com/render/math?math=\Large N_{Da}">  | <img src="https://render.githubusercontent.com/render/math?math=\Large \frac{K_aL^2}{D}">  | Contenido de la celda  |



### Meshing and solution schemes

## Results

## Conclusions

## References


## Appendix A. 

## Appendix B.
