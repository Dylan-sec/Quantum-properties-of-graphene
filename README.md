# ⚛ Quantum-properties-of-graphene

The objective of this program's design is to simply simulate the quantum properties of graphene that give it its unique electronic properties as a superconducting material.

---
 The Theory Behind Graphene :

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
 Network vector:

In each layer of graphene, the carbon atoms are arranged in a hexagonal structure
in the unit cell (the simplest repeating pattern).

<img width="1255" height="830" alt="Capture d’écran 2026-01-28 145223_upscayl_5x_upscayl-standard-4x" src="https://github.com/user-attachments/assets/d6295dfa-6dc5-49cf-9136-d2b1e4f9682d" />
<img width="850" height="755" alt="Capture d’écran 2026-01-28 145244_upscayl_5x_upscayl-standard-4x" src="https://github.com/user-attachments/assets/9773866b-e82a-4d7b-997d-b6fc34c9555a" />


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
