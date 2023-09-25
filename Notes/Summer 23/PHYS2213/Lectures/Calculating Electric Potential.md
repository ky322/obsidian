23.3-5
If you are given a continuous charge distribution, devise a way to divide it into infinitesimal elements

### Example 23.8 A Charged Conducting Sphere 
A solid conducting sphere of radius $R$ has a total charge $q$. Find the electric potential everywhere, inside and outside the sphere. 

Take $V=0$ at infinity as for a point charge
Potential at a point outside the sphere at a distance $r$ from its center is the same as that due to ap point charge $q$ at the center
$$V={1\over4\pi\epsilon_0}{q\over r}$$
$$V_{\text{surface}}={q\over4\pi\epsilon_0R}$$
Inside: 
$\vec{E}=0$ so no work is done on a test charge that moves from any point to another point inside the sphere. The potential is the same at every point inside the sphere and is equal to ${q\over4\pi\epsilon_0R}$ at the surface. 

### Example 23.9 Oppositely Charged Parallel Plates 
Find the potential at any height $y$ between the two oppositely charged parallel plates. 
$$U=q_0Ey$$$$V(y)={U(y)\over q_0}={q_0Ey\over q_0}=Ey$$
$$V_a-V_b=Ed\rightarrow E={V_{ab}\over d}$$

### Example 23.10 An Infinite Line Charge or Charged Conducting Cylinder 
Find the potential at a distance $r$ from a very long line of charge with linear charge density $\lambda$
$$V_a-V_b=\int_a^b\vec{E}\cdot d\vec{l}=\int_a^b E_rdr={\lambda\over2\pi\epsilon_0}\int^{r_b}_{r_a}{dr\over r}={\lambda\over2\pi\epsilon_0}\ln{r_b\over r_a}$$
Set $V_b=0$ at point $b$ at an arbitrary but finite radial distance $r_0$ then $V=V_a$ at point $a$ at a radial distance $r$ is given by $$V-0=V={\lambda\over2\pi\epsilon_0}\ln{r_0\over r}$$
$V$ decreases as we move in the direction of $\vec{E}$

### Example 23.11 A Ring of Charge 
Electric charge $Q$ is distributed uniformly around a thin ring of radius $a$. Find the potential at a point $P$ on the ring axis at a distance $x$ from the center of the ring.

Divide the ring into infinitesimal segments and find $V$
$$\begin{align}
V&={1\over4\pi\epsilon_0}\int{dq\over r}\\
&={1\over4\pi\epsilon_0}{1\over\sqrt{x^2+a^2}}\int{dq}\\
&={1\over4\pi\epsilon_0}{Q\over\sqrt{x^2+a^2}}
\end{align}$$
### Example 23.12 Potential of a Line of Charge 
Positive electric charge $Q$ is distributed uniformly along a line of length $2a$ lying along the y-axis between $y=-a$ and $y=+a$. Find the electric potential at point $P$ on the a-axis at a distance $x$ from the origin. 

$$dQ={Q\over2a}dy$$
$$dV={1\over4\pi\epsilon_0}{Q\over2a}{dy\over\sqrt{x^2+y^2}}$$
$$V={1\over4\pi\epsilon_0}{Q\over2a}
\int_{-a}^a{dy\over\sqrt{x^2+y^2}}$$
$$V={1\over4\pi\epsilon_0}{Q\over2a}
\ln\left({\sqrt{a^2+y^2}+a\over\sqrt{a^2+y^2}-a}\right)$$

## Equipotential Surfaces
Equipotential surface: three dimensional surface where the electric potential is the same at each point 

Potential energy does not change as a test charge moves over a equipotential surface, hence the electric field can do no work 

$\vec{E}$ must be perpendicular to the surface at every point so $q_0\vec{E}$ is perpendicular to the displacement of a charge moving on the surface 

Field Lines and equipotential surfaces are perpendicular 

In regions where the magnitude of $\vec{E}$ is large, the equipotential surfaces are close together because the field does large work on a test charge 

When all charges are at rest, the surface of a conductor is an equipotential surface
When all charges are at rest, the electric field outside a conductor must be perpendicular to the surface at every point 
When all the charges are at rest, the entire solid volume of a conductor is at the same potential 

## Potential Gradient 
Electric Field Components Found from Potential
$$E_x=-{\partial V\over\partial x}\Rightarrow\vec{E}=-\left(\hat{i}{\partial V\over\partial x}+\hat{j}{\partial V\over\partial y}+\hat{k}{\partial V\over\partial z}\right)$$
Gradient: $$\vec{\nabla}f=\left(\hat{i}{\partial\over\partial x}+\hat{j}{\partial\over\partial y}+\hat{k}{\partial\over\partial z}\right)f\Rightarrow\vec{E}=-\vec{\nabla}V$$
At each point, the potential gradient $\vec{\nabla}V$ points in the direction in which V increases
most rapidly with a change in position

## Example 23.13 Potential and field of a point charge
The potential at a radial distance $r$ from a point charge $q$ is $V={q\over4\pi\epsilon_0r}$. Find the vector electric field from this expression for $V$
$$E_r = -{\partial V\over\partial r}=-{\partial\over\partial r}\left({1\over4\pi\epsilon_0}{q\over r}\right)={1\over4\pi\epsilon_0}{q\over r^2}$$
$$\vec{E}=\hat{r}E_r={1\over4\pi\epsilon_0}{q\over r^2}\hat{r}$$
### Example 23.14 Potential and Field of a Ring of Charge 
For a ring of charge with radius $a$ and total charge $Q$ the potential at a point $P$ on the ring's symmetry axis at a distance $x$ from the center is $$V={1\over4\pi\epsilon_0}{Q\over\sqrt{x^2+a^2}}$$Find the electric field at $P$
$$E_x=-{\partial V\over\partial x}={1\over4\pi\epsilon_0}{Q\over(x^2+a^2)^{3\over2}}$$
