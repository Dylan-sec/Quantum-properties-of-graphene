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
III) Calculation of the Hamiltonian:

The Hamiltonian of graphene pz orbitals can be described using the tight-binding method (or LCAO method), in which the Hamiltonian operator of graphene is described by:
In the pz orbital basis, denoted |i> with i as the atomic index, the Hamiltonian is represented by a Hamiltonian matrix whose elements hij=tij include only interactions between electrons of the same type.


<img width="351" height="47" alt="image" src="https://github.com/user-attachments/assets/b131d3e6-54fa-42bf-8a71-3c2ee69a2a95" />


In the basis of pz orbitals, denoted |i> with i as the atomic index, the Hamiltonian is represented by a Hamiltonian matrix whose elements: hij=tij include only interactions
(or cutoff) of first neighbors, i.e., those that form direct bonds between them. If
orbital i and j are neighbors, then tij = 2.7 eV; otherwise, tij = 0.

To calculate the elements hij of the matrix, we must set the condition that if the distance
between the carbon atoms is less than 0.6*a, then hij is equal to 2.7 eV (if d < 0.6a:
h[i][j]=2.7), with a being the lattice parameter a = 0.2456 nm.
If the distance is greater than 0.6a, then hij is equal to 0 eV (else: h[i][j]= 0).

---
IV)  Diagonalization of the Hamiltonian matrix

We are looking for a basis in which the Hamiltonian matrix of graphene is diagonal.
So the first step will be to determine the eigenvalues, i.e., the eigenenergies
of the system and the eigenvectors associated with these energies:
<img width="100" height="48" alt="image" src="https://github.com/user-attachments/assets/fb4c971e-73db-48a9-a54d-c7743fe6edf8" />
for n={0, ... , N-1} , N is the total number of orbitals in the system under study.

To verify that these are indeed eigenstates, we will then check that the norm of the vector A: ||A||=||H0|n>-En|n>||=0
If the norm is equal to zero, the Hamiltonian matrix is indeed diagonal in the basis of the states |n>.

So, to obtain the norms of A for different eigenvectors (values of n), we first
determine the norm from the first eigenvector |n=1>, which we have called A0
(norm_A0=np.sqrt((A[0])**2)), and then add the norms of the other eigenvectors |n=1>,
 which we call An (Norm_An=np.sqrt(np.sum((A[p])**2)), which allows us to obtain the
norm as a function of the number of eigenvectors.

---
V) Clean states and their evolution in a time-independent potential:

Diagonalizing the Hamiltonian matrix allows us to determine the eigenstates of the
system at time t (which we will denote <img width="30" height="30" alt="image" src="https://github.com/user-attachments/assets/3cb15ccc-399a-4ee7-9a8d-7541908121d9" />) from an eigenstate at an initial time t0 <img width="35" height="35" alt="image" src="https://github.com/user-attachments/assets/0fde4baa-4624-4d90-97e6-5aa1a476e0d9" />. Since the Hamiltonian operator H is independent of time, we will use
the time evolution operator: therefore, to find the eigenstates
at t: <img width="177" height="26" alt="image" src="https://github.com/user-attachments/assets/cc7e3e72-95ba-4125-8415-3894cb33bd2e" />

To calculate the evolution operator U, we used a function from the
Scipy library called expm, which allows us to calculate the matrix exponential
of a matrix. This function itself performs the changes to a matrix basis
(an essential and time-consuming step in calculating the matrix exponential). So we
write the evolution operator U (U=expm(-1j*h*(t-t0)/ħ) with j a complex number “i”
imaginary, t0 the time at the initial moment, t the time in seconds, and ħ the Planck constant).

In the code and the rest of this report, we consider the variable T =(t-t0)/ħ to simplify
the notation of time. So for a Hamiltonian in eV, T is in eV-1 and the time in seconds is t-t0 = T*h (eVs) = 1.054 571 818 × 10−34/1.602 176 634 × 10−19 =6.582119572*10-16 eVs ) and then perform the calculation of <img width="45" height="27" alt="image" src="https://github.com/user-attachments/assets/77f61bac-d173-470c-b2bb-1f45d5f5d4c0" /> by performing the matrix product of <img width="65" height="27" alt="image" src="https://github.com/user-attachments/assets/1546a8a0-204c-47ca-b3c0-53a843ea5660" /> and <img width="120" height="47" alt="image" src="https://github.com/user-attachments/assets/10d6205e-40a4-4fc3-accd-fc7e95a69d2c" /> (vecp_T=np.dot(U,vecp_initial)).

---


