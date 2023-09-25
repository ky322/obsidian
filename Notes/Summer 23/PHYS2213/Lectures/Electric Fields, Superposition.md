The electric force on a charged object is exerted by the electric field created by other charged objects 

Test Charge: A small charged object to test whether there is an electric field at a particular point 

The electric field $\vec{E}$ at a point is the electric force $\vec{F}_0$ experienced by a test charge $q_0$ at the point divided by the charge $q_0$ $$\vec{E}=\frac{\vec{F_0}}{q_0}$$
The electric field $\vec{E}$ does not depend on the charge of the object on which the electric force is exerted. $$\hat{r}=\frac{\vec{r}}{r}$$
Electric Field due to a Point Charge: $$\vec{E}=\frac{1}{4\pi\epsilon_0}\frac{q}{r^2}\hat{r}$$
The electric field of a point charge always points away from a positive charge (in the same direction as $\hat{r}$) but towards a negative charge (the direction opposite $\hat{r}$)

Vector Field: $\vec{E}$ can be an infinite set of vector quantities 

If the magnitude and the direction of the field has the same values everywhere throughout a region the field is uniform in this region.

If there is an electric field within a conductor the field exerts a force on every charge in the conductor giving the free charges a net motion
- In electrostatics the electric field at every point within the material of a conductor must be 0

In electric interactions:
1. A given charge distribution acts as a source of electric field
	- Calculate the field caused by a source charge distribution
2. The electric field exerts a force on any charge that is present in the field
	- Look at the effect of the field in terms of force and motion 

### Example 21.5 Electric-Field Magnitude for a Point Charge 
What is the magnitude of the electric field $\vec{E}$ at a field point $2.0\space\mathrm{m}$ from a point charge $q=4.0\space\mathrm{nC}$?
$$\begin{align}
\vec{E}&=\frac{1}{4\pi\epsilon_0}\frac{q}{r^2}\hat{r} \\&=(9.0\times10^9\space\mathrm{N\cdot m^2/C^2})\frac{4.0\times10^{-9}\space\mathrm{C}}{(2.0\space\mathrm{m})^2}\\&=9.0\space\mathrm{N/C}
\end{align}$$
The result $E=0.0\space\mathrm{N/C}$ indicates that if we placed a $1.0\space\mathrm{C}$ charge at a point $2.0\space\mathrm{m}$ from $q$ it would experience a $9.0\space\mathrm{N}$ force. The force on a $2.0\space\mathrm{C}$ charge at that point would be $18\space\mathrm{N}$

The magnitude of the electric field that a point charge produces at a given point is proportional to the magnitude of the charge and inversely proportional to the square of the distance from the point charge to the point where the field is measured. 

### Example 21.6 Electric-Field Vector for a Point Charge 
A point charge $q=-8.0\space\mathrm{nC}$ is located at the origin. Find the electric-field vector at the field point $x=1.2\space\mathrm{m},y=-1.6\space\mathrm{m}$

The distance from $S$ to $P$: $r=\sqrt{(1.2\space\mathrm{m})^2+(-1.6\space\mathrm{m})^2}=2.0\space\mathrm{m}$
$$\hat{r}=\frac{\vec{r}}{r}=\frac{x\hat{i}+y\hat{j}}{r}=\frac{(1.2\space\mathrm{m})\hat{i}+(1.6\space\mathrm{m})\hat{j}}{2.0\space\mathrm{m}}=0.60\hat{i}-0.80\hat{j}$$
$$\begin{align}
\vec{E}&=\frac{1}{4\pi\epsilon_0}\frac{q}{r^2}\hat{r} \\&=(9.0\times10^9\space\mathrm{N\cdot m^2/C^2})\frac{-8.0\times10^{-9}\space\mathrm{C}}{(2.0\space\mathrm{m})^2}(0.60\hat{i}-0.80\hat{j})\\&=-11\space\mathrm{N/C}\hat{i}+14\space\mathrm{N/C}\hat{j}
\end{align}$$

### Superposition of Electric Fields 
The total electric field at a point $P$ is the vector sum of all the fields at $P$ due to each point charge in the charge distribution

Linear Charge Density $\lambda$: A line charge distribution
Surface Charge Density $\sigma`$: Charge distribution over a surface`
Volume Charge Density $\rho$: Charge distributed through a volume

### Example 21.9 Field of a Ring of Charge 
Charge $Q$ is uniformly distributed around a conducting ring of radius $a$. Find the electric field at a point $P$ on the ring axis a distance $x$ from its center. 

Divide the ring into infinitesimal segments $ds$: $$\lambda=\frac{Q}{2\pi a}\Rightarrow dQ=\lambda ds$$
The net field at $P$ us along the x-axis due to symmetry: $\vec{E}=E_x\hat{i}$

The magnitude of a segments contribution $d\vec{E}$ to the electric field at $P$ is: $$dE=\frac{1}{4\pi\epsilon_0}\frac{dQ}{x^2+a^2}$$
The x-component of this field is $dE_x=dE\cos\alpha$ and $$\cos\alpha=\frac{x}{r}=\frac{x}{(x^2+a^2)^{1/2}}$$ $$dE_x=dE\cos\alpha=\frac{1}{4\pi\epsilon_0}\frac{dQ}{x^2+a^2}\frac{x}{\sqrt{x^2+a^2}}=\frac{1}{4\pi\epsilon_0}\frac{\lambda x}{(x^2+a^2)^{3/2}}$$
Integrate to find $E_x$:
$$E_x=\int dE_x=\frac{1}{4\pi\epsilon_0}\frac{\lambda x}{(x^2+a^2)^{3/2}}\int^{2\pi a}_{0}ds=\frac{1}{4\pi\epsilon_0}\frac{\lambda x}{(x^2+a^2)^{3/2}}(2\pi a)$$
$$\vec{E}=E_x\hat{i}=\frac{1}{4\pi\epsilon_0}\frac{Qx}{(x^2+a^2)^{3/2}}\hat{i}$$
Key Concept: To find the vector components of the net electric field at a point due to a continuous distribution of charge:
1. Divide the distribution into infinitesimally small segments.
2. Find the components of the field at the point due to one such segment 
3. Integrate each component of the field due to a segment over all the segments in the charge distribution 

### Example 21.10 Field of a Charged Line Segment
Positive charge $Q$ is distributed uniformly along the y-axis between $y=-a$ and $y=+a$. Find the electric field at point $P$ on the x-axis at a distance $x$ from the origin 

Divide the line charge of length $2a$ into infinitesimal segments of length $dy$. The linear charge density is $\lambda=\frac{Q}{2a}$
The charge in a segment is $dQ=\lambda dy=\frac{Q}{2a}dy$
The distance $r$ from a segment at height $y$ to the field point $P$ is $r=(x^2+y^2)^{1/2}$
The magnitude of the field at $P$ due to the segment at height $y$ is $$dE=\frac{1}{4\pi\epsilon_0}\frac{dQ}{r^2}=\frac{1}{4\pi\epsilon_0}\frac{Q}{2a}\frac{dy}{(x^2+y^2)}$$
$$dE_x=dE\cos\alpha=\frac{1}{4\pi\epsilon_0}\frac{Q}{2a}\frac{xdy}{(x^2+y^2)^{3/2}}$$
By symmetry this is 0:$$dE_y=-dE\sin\alpha=-\frac{1}{4\pi\epsilon_0}\frac{Q}{2a}\frac{ydy}{(x^2+y^2)^{3/2}}$$
To find the total field at $P$ sum the fields from all segments: $$E_x=\frac{1}{4\pi\epsilon_0}\frac{Q}{2a}\int_{-a}^a\frac{xdy}{(x^2+y^2)^{3/2}}=\frac{Q}{4\pi\epsilon_0}\frac{1}{x\sqrt{x^2+a^2}}$$
$$E_y=-\frac{1}{4\pi\epsilon_0}\frac{Q}{2a}\int_{-a}^a\frac{ydy}{(x^2+y^2)^{3/2}}=0$$
In vector form: $$\vec{E}=\frac{1}{4\pi\epsilon_0}\frac{Q}{x\sqrt{x^2+a^2}}\hat{i}$$
### Example 21.11 Field of a Uniformly Charged Disk 
A nonconducting disk of radius $R$ has a uniform positive surface charge density of $\sigma$. Find the electric field at a point along the axis of the disk a distance $x$ from its center. Assume that $x$ is positive.

A typical ring has charge $dQ$ so the charge per unit area is $\sigma=\frac{dQ}{dA}\Rightarrow dQ=\sigma dA=2\pi\sigma rdr$

The field component $dE_x$ at point $P$ due to all the ring is $$dE_x=\frac{1}{4\pi\epsilon_0}\frac{2\pi\sigma rxdr}{(x^2+r^2)^{3/2}}$$To find the total field due to all the rings we integrate $dE_x$ over $r$ from $r=0$ to $r=R$ $$E_x=\int_0^R\frac{1}{4\pi\epsilon_0}\frac{(2\pi\sigma rdr)x}{(x^2+r^2)^{3/2}}=\frac{\sigma x}{4\epsilon_0}\int_0^R\frac{2rdr}{(x^2+r^2)^{3/2}}$$ $$E_x=\frac{\sigma x}{2\epsilon_0}[-\frac{1}{\sqrt{x^2+R^2}}+\frac{1}{x}]$$
$$E_x=\frac{\sigma x}{2\epsilon_0}\Big[1-\frac{1}{\sqrt{\frac{R^2}{x^2}+1}}\Big]$$
