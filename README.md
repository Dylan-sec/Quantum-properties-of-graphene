# ⚛ Quantum-properties-of-graphene

The objective of this program's design is to simply simulate the quantum properties of graphene that give it its unique electronic properties as a superconducting material.

---
 I: The Theory Behind Graphene :

First named in 1789 as “graphite” by German mineralogist
Abraham Gottlob Werner, theorized in 1947 by physicist P.R. Wallace, then isolated for the
first time by A. Geim and his team [1]. Graphene is a two-dimensional hexagonal lattice of carbon atoms that resembles a honeycomb.

The carbon atom has 6 electrons, 4 of which are in its outer shell (known as valence electrons). Thecarbon atoms that make up the crystal structure of graphene are each sp2 hybridized,
a hybridization that results from the combination of the 2s, 2px, and 2py orbitals, which form 3
hybrid orbitals, each with a probability of electron presence in a given direction
that is strong in the (xy) plane, rotated 120° relative to each other, and then a
2pz orbital perpendicular to the plane that does not participate in covalent bonds with the
other carbon atoms.

<img width="2885" height="1035" alt="Capture d’écran 2026-01-28 144327_upscayl_5x_upscayl-standard-4x" src="https://github.com/user-attachments/assets/0f4885ff-e57f-4bcb-8d1a-8cb9fe5cde1d" />

Materials based on sp2 hybridized carbon can be classified into several forms depending on the
dimension they occupy in which they extend in space:

<img width="3940" height="1110" alt="Capture d’écran 2026-01-28 144525_upscayl_5x_upscayl-standard-4x" src="https://github.com/user-attachments/assets/bd4a178f-6413-482e-aea8-6713141ac4df" />

Graphene synthesis:

Graphene manufacturing methods can be classified into two types according to the extraction method:
- Exfoliated graphene, which involves using adhesive tape to peel off thin
layers of graphite, then folding and refolding the tape several times until
very thin layers of graphite are obtained, which are then placed on a silicon oxide substrate
to find a layer of graphene among the thin layers of
graphite. (Geim method) [1].

- Epitaxial graphene, which involves manufacturing graphene from a silicon carbide (SiC) crystal
heated in a vacuum to 1300°C, which evaporates, leaving only carbon atoms on the surface
that together form thin layers of graphene. (De Heer method).

<img width="1610" height="1050" alt="Capture d’écran 2026-01-28 144814_upscayl_5x_upscayl-standard-4x" src="https://github.com/user-attachments/assets/b194f2d6-689e-4674-afd3-552bc7e10aec" />

New methods have been developed, such as:
- CVD (which involves decomposing methane on a metal heated to high temperatures).

- Chemical method (involves oxidizing graphite in sulfuric acid using
hydrazine as a reducing solvent).

---
II) Network vector:

In each layer of graphene, the carbon atoms are arranged in a hexagonal structure
in the unit cell (the simplest repeating pattern).

<img width="1255" height="800" alt="Capture d’écran 2026-01-28 145223_upscayl_5x_upscayl-standard-4x" src="https://github.com/user-attachments/assets/d6295dfa-6dc5-49cf-9136-d2b1e4f9682d" />
<img width="850" height="800" alt="Capture d’écran 2026-01-28 145244_upscayl_5x_upscayl-standard-4x" src="https://github.com/user-attachments/assets/9773866b-e82a-4d7b-997d-b6fc34c9555a" />


We have two basis vectors, which we will denote a and b, with coordinates a (0.1)*a and b (-1⁄2*,
√(3/2))*a, where a is the graphene lattice parameter a = 0.246 nm, describing a
translation of the lattice t=n*a+m*b (n and m are integers) as the translation vector
only allows us to have the positions of carbon atoms belonging to the same
lattice, and since the graphene pattern is composed of two atoms, we define a vector c with the
coordinates of the carbon atom c (1/2,(1/(√3)*2))*a not belonging to the lattice and we
thus obtain the new positions R=n*a+m*b+c.

Using the Python programming language library “Numpy,” we can write the
translation vector t = (r = a*n1 + b*n2 ), which gives us the position of the carbon atoms
belonging to the lattice, and R (r = a*n1 + b*n2 +np.array([1/2, 1/(np.sqrt(3)*2)]) for
those that do not belong to the lattice. We then create a table that will contain the positions
of the carbon atoms with a column with the coordinates x=t[n][0] and y = t[n][1].

---
II) Calculation of the Hamiltonian:


The Hamiltonian of the $p_z$ orbitals in graphene can be described using the **Tight-Binding Method** (or LCAO), where the graphene Hamiltonian operator is defined as:

$$\hat{H} = \sum_{\langle i,j \rangle} -t |i\rangle \langle j| \quad \text{with } t = 2.7 \text{ eV}$$

In the basis of the $p_z$ orbitals, denoted as $|i\rangle$ (where $i$ is the atom index), the Hamiltonian is represented by a matrix whose elements $h_{ij} = t_{ij}$ only include nearest-neighbor interactions (or coupling). 

These represent atoms that form direct bonds : if orbitals $i$ and $j$ are neighbors, then $t_{ij} = 2.7 \text{ eV}$, otherwise $t_{ij} = 0$.

To calculate the $h_{ij}$ elements of the matrix, we set the condition.

The hopping condition is defined as :

$$h_{ij} = 
\begin{cases} 
2.7 \text{ eV} & \text{if } d_{ij} < 0.6a \\
0 \text{ eV} & \text{otherwise}
\end{cases}$$

---
III) Calculation of the Hamiltonian:

We are looking for a basis in which the Hamiltonian matrix of graphene is diagonal, so the first step will be to determine the eigenvalues, i.e., the eigenvalues of the system and the eigenvectors associated with these energies: 

$$\hat{H}_0 |n\rangle = E_n |n\rangle$$

for $n=\{0, \dots , N-1\}$

where $N$ is the total number of $p_z$ orbitals in the system under study.

To verify that these are indeed eigenstates, we will then check that the norm of vector $A$: 

$$\|A\| = \| \hat{H}_0 |n\rangle - E_n |n\rangle \| = 0$$

If the norm is equal to zero, the Hamiltonian matrix is indeed diagonal in the basis of states $|n\rangle$.

So, to obtain the norms of $A$ for different eigenvectors (values of $n$), we first determine the norm from the first eigenvector $|n=1\rangle$, which we call $A_0$:

$$\text{norm} A_0 = \sqrt{(A[0])^2}$$

and then add the norms of the other eigenvectors $|n=1\rangle$

which we call $A_n$:

$$\text{Norm} A_n = \sqrt{\sum (A[p])^2}$$

This allows us to obtain the norm as a function of the number of eigenvectors.

---
IV) Eigenstates and their Evolution in a Time-Independent Potential

The diagonalization of the Hamiltonian matrix allows us to determine the eigenstates of the system at time $t$ (denoted $|\psi(t)\rangle$) starting from an initial eigenstate at time $t_0$ ($|\psi(t_0)\rangle$). Since the Hamiltonian operator $\hat{H}$ is time-independent, we use the time-evolution operator $U(t, t_0)$:

$$U(t, t_0) = e^{-\frac{i}{\hbar} \hat{H} \times (t-t_0)}$$

To find the eigenstate at time $t$: 
$$|\psi(t)\rangle = U(t, t_0) |\psi(t_0)\rangle$$

To calculate the evolution operator $U$, we utilize the `expm` function from the **SciPy** library, which computes the matrix exponential. This function handles the essential and complex step of changing the matrix basis to perform the calculation. 

To simplify the code, we consider the variable $T = (t - t_0) / \hbar$. For a Hamiltonian in eV, $T$ is in $\text{eV}^{-1}$ and time in seconds is $t - t_0 = T \times \hbar$. Finally, $|\psi(t)\rangle$ is calculated via the matrix product

To calculate the evolution operator U, we used a function from the
Scipy library called expm, which allows us to calculate the matrix exponential
of a matrix. This function itself performs the changes to a matrix basis
(an essential and time-consuming step in calculating the matrix exponential). 

So we write the evolution operator $$U(t, t_0) = e^{-\frac{i}{\hbar} \hat{H} (t-t_0)}$$

In the Python implementation, this operator is calculated using the `expm` function from the SciPy library:

#### Variables Definition:
* **$j$**: The imaginary complex number (equivalent to $i$ in physics notation).
* **$t_0$**: The initial time.
* **$t$**: The time in seconds.
* **$\hbar$**: The reduced Planck constant.
* **$h$**: The Hamiltonian matrix.

In the code and throughout this report, we use the variable $T = (t-t_{0})/\hbar$ to simplify the expression of time. 

Thus, for a Hamiltonian expressed in eV, $T$ is in $\text{eV}^{-1}$ and the time in seconds is given by:
$$t-t_{0} = T \times \hbar \text{ (eV}\cdot\text{s)}$$

The calculation of $|\psi(t)\rangle$ is then performed by taking the matrix product of the initial state $|\psi(t_{0})\rangle$ and the time-evolution operator $U(t,t_{0}) = e^{-\frac{i}{\hbar}\hat{H} \times (t-t_0)}$:

---
**Modeling and Results**
---
V) Modeling the structure of graphene
---
Here is our graphene ribbon containing 261 carbon atoms:

<img width="2865" height="2115" alt="Capture d’écran 2026-01-28 174112_upscayl_5x_upscayl-standard-4x" src="https://github.com/user-attachments/assets/c6b4b8aa-134d-496d-b309-3eed8225f93d" />

Graphene ribbon with a width
l = 19 Å and a length L = 34 Å
---

VI) Modeling the evolution over time of a state specific to time T0 and T

In this modeling of the eigenstate at the initial time T0 and the eigenstate at time
T=100, we have chosen and that of the orbital at coordinate (-7;0), and we note that the
probability of the presence of the eigenstate of our orbital does not change over time. This
is normal because an eigenstate of the Hamiltonian is invariant over time.
