Positive charge inside the box goes with an outward electric flux through the box's surface; negative charge inside the box goes with an inward electric flux through the box's surface

If there are zero charge inside the box, $\vec{E}=0$ everywhere so there is no electric flux into or out of the box 

The net electric flux through the surface of the box is directly proportional to the magnitude of the net charge enclosed by the box; this is independent of the size of the box 

For the cases of a closed surface in the shape of a rectangular box and charge distributions made up of point charges of infinite charged sheets:
1. Whether there is a net outward or inward electric flux through a closed surface depends on the sign of the enclosed charge 
2. Charges outside the surface do not give a net electric flux through the surface 
3. The net electric flux is directly proportional to the net amount of charge enclosed within the surface but is independent of the size of the closed surface

## Calculating Electric Flux
For a flat surface and a uniform electric field, the electric flux is: $$\Phi_E=EA=EA\cos\phi=E_\perp A=\vec{E}\cdot\vec{A}$$
Increasing area means more lines of $\vec{E}$ can pass through the area which increases flux
A stronger field means more closely spaced lines of $\vec{E}$ and more lines per unit area so flux increases
Electric Flux SI Units: $1\space\mathrm{N\cdot m^2/C}$
We can represent the direction of a vector area $\vec{A}=A\hat{n}$ where $\hat{n}$ is the normal 
Flux of a nonuniform electric field: $$\Phi_E=\int E\cos\phi dA=\int E_\perp dA=\int\vec{E}\cdot d\vec{A}$$
### Example 22.1 Electric Flux Through a Disk
A disk of radius $0.10\space\mathrm{m}$ is oriented with its normal unit vector $\hat{n}$ at $30\degree$ to a uniform electric field $\vec{E}$ of magnitude $2.0\times 10^3\space\mathrm{N/C}$. What is the electric flux through the disk? 
$A=0.0314\space\mathrm{m^2},\phi =30\degree$
$$\Phi_E=EA\cos\phi=(2.0\times10^3\space\mathrm{N/C})(0.0314\space\mathrm{m^2})(\cos30\degree)=54\space\mathrm{N\cdot m^2/C}$$
What is the flux through the disk if it is turned so that $\hat{n}$ is perpendicular to $\vec{E}$? 
$$\phi=90\degree,\cos\phi=0\Rightarrow\Phi_E=0$$
What is the flux through the disk if $\hat{n}$ is parallel to $\vec{E}$?
$$\Phi_E=EA\cos\phi=(2.0\times10^3\space\mathrm{N/C})(0.0314\space\mathrm{m^2})(\cos0\degree)=63\space\mathrm{N\cdot m^2/C}$$
### Example 21.2 Electric Flux Through a Cube
An imaginary cubical surface of side $L$ is in a region of uniform electric field $\vec{E}$. Find the electric flux when:
The cube is oriented with two of its faces perpendicular to $\vec{E}$
$$\begin{align}
\Phi_{E1}=\vec{E}\cdot\hat{n}_1A=EL^2\cos180\degree=-EL^2\\\Phi_{E2}=\vec{E}\cdot\hat{n}_2A=EL^2\cos0\degree=EL^2\\\Phi_{E3}=\Phi_{E4}=\Phi_{E5}=\Phi_{E6}=\vec{E}\cdot\hat{n}_1A=EL^2\cos90\degree=0\\
\Phi_E=-EL^2+EL^2+0+0+0+0=0
\end{align}$$
The cube is turned by an angle $\theta$ about a vertical axis
$$\begin{aligned}
\Phi_{E1}=\vec{E}\cdot\hat{n}_1A=EL^2\cos(180\degree-\theta)=-EL^2\cos\theta\\\Phi_{E2}=\vec{E}\cdot\hat{n}_2A=EL^2\cos\theta\\\Phi_{E3}=\vec{E}\cdot\hat{n}_3A=EL^2\cos(90\degree-\theta)=-EL^2\sin\theta\\\Phi_{E4}=\vec{E}\cdot\hat{n}_4A=EL^2\cos(90\degree-\theta)=EL^2\sin\theta
\\\Phi_{E5}=\Phi_{E6}=EL^2\cos90\degree=0\\
\Phi_E=0
\end{aligned}$$
### Example 22.3 Electric Flux Through a Sphere 
A point charge $q=3.0\space\mathrm{\mu C}$ is surrounded by an imaginary sphere of radius $r=0.20\space\mathrm{m}$ centered on the charge. Find the resulting electric flux through the sphere.
$$\begin{align}
\Phi_E&=\int EdA\Rightarrow E\int dA=EA=\frac{q}{4\pi\epsilon_0r^2}4\pi r^2=\frac{q}{\epsilon_0}\\&=\frac{3.0\times10^{-6}\space\mathrm{C}}{8.85\times10^{-12}\space\mathrm{C^2/N\cdot m^2}}=3.4\times10^5\space\mathrm{N\cdot m^2/C}
\end{align}$$
## Gauss's Law 
The total electric flux through any closed surface is proportional to the total net electric chaarge inside the surface. 
The flux is independent of the radius $R$ of the sphere. It only depends on the charge $q$ enclosed by the sphere. 
$$\Phi_E=\oint\vec{E}\cdot d\vec{A}={Q_{\text{encl}}\over\epsilon_0}$$
The total electric flux through a closed surface is equal to the total net electric charge inside the surface divided by $\epsilon_0$
$$\Phi_E=\oint\vec{E}\cdot d\vec{A}={Q_{\text{encl}}\over\epsilon_0}=\oint E\cos\phi dA=\oint E_\perp dA$$
## Applications of Gauss's Law 
Gauss's Law is valid for any distribution of charges and for any closed surfaces. 
When excess charge is placed on a solid conductor and is at rest it resides entirely on the surface not in the interior of the material.
There can be no excess charge at any point within a solid conductor; any excess charge must reside on the conductor's surface.

### Example 22.6 Field of A Uniform Line Charge 
Electric charge is distributed uniformly along an infinitely long thin wire. The charge per unit length is $\lambda$. Find the electric field by using Gauss's law. 

The flux through the flat ends of the Gaussian surface is zero because the radial electric field is parallel to these ends so $\vec{E}\cdot\hat{n}=0$. 
On the cylindrical part of the surface $\vec{E}\cdot\hat{n}=E_\perp\Rightarrow EA=2\pi rlE$
$Q_{\text{encl}}=\lambda l$
$$\Phi_E=2\pi rlE={\lambda l\over\epsilon_0}$$
$$E={1\over2\pi\epsilon_0}{\lambda\over r}$$
To use Gauss's law to a charge distribution with a cylindrical symmetry (infinite line or cylinder of charge) use cylindrical Gaussian surface. At all points on the curved sides of the surface the electric field has the same magnitude and is normal to the surface. On the flat ends of the cylindrical surface the electric field is parallel to the surface so the flux through the ends is zero. 

### Example 22.7 Field of an Infinite Plane Sheet of Charge 
Find the electric field caused by a thin flat infinite sheet with uniform positive surface charge density $\sigma$
The flux through the cylindrical part of the Gaussian surface is zero because $\vec{E}\cdot\hat{n}=0$. 
The flux through each flat end of the surface is $EA$ because $\vec{E}\cdot\hat{n}=E_\perp=E$
The total flux through the Gaussian surface is $2EA$
The total enclosed charge is $Q_{\text{encl}}=\sigma A$$$2EA={\sigma A\over\epsilon_0}\Rightarrow E={\sigma\over2\epsilon_0}$$
To apply Gauss's Law to a charge distribution with planar symmetry (infinite sheet of charge) use a Gaussian surface. At all points on the flat ends of the surface, the electric field has the same magnitude and is normal to the surface. On the curved sides of the cylindrical surface, the electric field is parallel to the surface so the flux through the sides is zero.

