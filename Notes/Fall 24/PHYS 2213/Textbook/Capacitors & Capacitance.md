Capacitor: Any two conductors separated by an insulator 
Capacitance $C$ of the capacitor: Ratio of charge to potential difference $$C={Q\over V_{ab}}$$
SI Unit: $1\space\mathrm{F}=1\space\mathrm{C/V}, 1\space\mathrm{\mu F}=10^{-6}\space\mathrm{F},1\space\mathrm{pF}=10^{-12}\space\mathrm{F}$

Capacitance is a measure of the ability of a capacitor to store energy 
Capacitance of a Parallel-Plate capacitor in vacuum: $$C={Q\over V_{ab}}=\epsilon_0{A\over d}$$
For any capacitor in vacuum, $C$ depends only on the shapes, dimensions, and separation of the conductors that make up the capacitor.

### Example 24.1 Size of a $1\space\mathrm{F}$ Capacitor
The parallel plates of a $1.0\space\mathrm{F}$ capacitor are $1.0\space\mathrm{mm}$ apart. What is their area?
$$A={Cd\over\epsilon_0}={(1.0\space\mathrm{F})(1.0\times10^{-3}\space\mathrm{m})\over8.85\times10^{-12}\space\mathrm{F/m}}=1.1\times10^8\space\mathrm{m^2}$$

### Example 21.2 Properties of a Parallel-Plate Capacitor 
The plates of a parallel-plate capacitor in vacuum are $5.00\space\mathrm{mm}$ apart and $2.00\space\mathrm{m^2}$ in area. A $10.0\space\mathrm{kV}$ potential difference is applied across the capacitor. Compute:
Capacitance $$C=\epsilon_0{A\over d}=(8.85\times10^{-12}\space\mathrm{F/m}){(2.00\space\mathrm{m^2})\over5.00\times10^3\space\mathrm{m}}=3.45\times10^{-9}\space\mathrm{F}=0.00345\space\mathrm{\mu F}$$
Charge on Capacitor: $$Q=CV_{ab}=(3.54\times10^{-9}\space\mathrm{C/V})(1.00\times10^4\space\mathrm{V})=3.54\times10^{-5}\space\mathrm{C}=35.4\space\mathrm{\mu C}$$
Electric Field Magnitude: 
$$E={\sigma\over\epsilon_0}={Q\over\epsilon_0A}={3.54\times10^-5\space\mathrm{C}\over(8.85\times10^{-12}\space\mathrm{C^2/N\cdot m^2})(2.00\space\mathrm{m^2})}=2.00\times10^6\space\mathrm{N/C}$$

### Example 24.3 A Spherical Capacitor 
Two concentric spherical conducting shells are separated by vacuum. The inner shell has total charge $+Q$ and the outer radius $r_a$ and the outer shell has charge $-Q$ and inner radius $r_b$. Find the capacitance of this spherical capacitor. 
$$V_{ab}=V_a-V_b={Q\over4\pi\epsilon_0r_a}-{Q\over4\pi\epsilon_0r_b}={Q\over4\pi\epsilon_0}{r_b-r_a\over r_ar_b}$$

$$C={Q\over V_{ab}}=4\pi\epsilon_0{r_ar_b\over r_b-r_a}$$
To find the capacitance of any capacitor made up of two conductors, calculate the potential difference $V_{ab}$ between the two conductors when they carry charges $Q$ and $-Q$. Capacitance is equal to ${Q\over V_{ab}}$

### Example 24.2 A Cylindrical Capacitor
Two long coaxial cylindrical conductors are separated by vacuum. The inner cylinder has outer radius $r_a$ and linear charge density $+\lambda$. The outer cylinder has inner radius $r_b$ and linear charge density $-\lambda$. Find the capacitance per unit length for this capacitor. $$V_{ab}={\lambda\over2\pi\epsilon_0}\ln{r_b\over r_a}$$
Charge in a length $L$ is $Q=\lambda L$ $$C={Q\over V_{ab}}={\lambda L\over{\lambda\over2\pi\epsilon_0}\ln{r_b\over r_a}}={2\pi\epsilon_0L\over\ln(r_b/r_a)}$$
Capacitance per Unit Length: $${C\over L}={{2\pi\epsilon_0\over\ln(r_b/r_a)}}$$
Substituting in $\epsilon_0=8.85\times10^{-12}\space\mathrm{F/m}:$ $${C\over L}={55.6\space\mathrm{pF/m}\over\ln(r_b/r_a)}$$
The capacitance per unit length of two long coaxial conducting cylinders depends on the ratio of the inner radius of the outer conductor to the outer radius of the inner conductor

## Capacitors in Series and Parallel 

### Series:
The magnitude of charge on all plates is the same
The equivalent capacitance $C_{\text{eq}}$ is the capacitance of a single capacitor for which the charge $Q$ is the same as for the combination when the potential difference $V$ is the same. 
$${1\over C_{\text{eq}}}={1\over C_1}+{1\over C_2}+\cdots$$
The reciprocal of the equivalent capacitance of a series combination equals the sum of the reciprocals of the individual capacitances. The equivalent capacitance is less than any individual capacitance.
Potential Differences add 
$$V_{ab}=V=V_1+V_2=Q\Big({1\over C_1}+{1\over C_2}\Big)$$
$$C_{\text{eq}}={Q\over V}$$

### Parallel: 
The potential difference for all individual capacitors is the same $V_{ab}=V$
The charge on each capacitor depends on its capacitance $$Q_1=C_1V$$
Charge is the sum of the individual charges 
Equivalent capacitance: $C_{\text{eq}}=C_1+C_2+\cdots$

### Example 24.5 Capacitors in Series and in Parallel
Let $C_1=6.0\space\mathrm{\mu F}, C_2=3.0\space\mathrm{\mu F}, V_{\text{ab}}=18\space\mathrm{V}$.  Find the equivalent capacitance and the charge and potential difference for each capacitor when the capacitors are connected in series
$${1\over C_{\text{eq}}}={1\over C_1}+{1\over C_2}={1\over6.0\space\mathrm{\mu F}}+{1\over3.0\space\mathrm{\mu F}}\space C_{\text{eq}}=2.0\space\mathrm{\mu C}$$
$$Q=C_{\text{eq}}V=(2.0\space\mathrm{\mu F})(18\space\mathrm{V})=36\space\mathrm{\mu C}$$
$$V_{ac}=V_1={Q\over C_1}={36\space\mathrm{\mu C}\over6.0\space\mathrm{\mu F}}=6.0\space\mathrm{V}$$
$$V_{cb}=V_2={Q\over C_2}={36\space\mathrm{\mu C}\over3.0\space\mathrm{\mu F}}=12.0\space\mathrm{V}$$
in parallel
$$C_{\text{eq}}=C_1+C_2=6.0\space\mathrm{\mu F}+3.0\space\mathrm{\mu F}=9.0\space\mathrm{\mu F}$$
$$V=18\space\mathrm{V}$$
$$Q_1=C_1V=(6.0\space\mathrm{\mu F})(18\space\mathrm{V})=108\space\mathrm{\mu F}$$
$$Q_2=C_1V=(3.0\space\mathrm{\mu F})(18\space\mathrm{V})=54\space\mathrm{\mu F}$$
When capacitors are combined in series the charge is the same on each capacitor but the potential differences acorss the capacitor may not be the same. 
When capacitors are combined in parallel the potential differences across each capacitor are the same but the charges on the capacitor may not be the same. 



