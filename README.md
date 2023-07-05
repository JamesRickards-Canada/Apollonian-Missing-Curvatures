# Apollonian-Missing-Curvatures

This repository stores data related to curvatures that are admissible in a primitive Apollonian circle packing, but do not appear. Some of this data appears in the paper [The Local-Global Conjecture for Apollonian circle packings is false](). It was computed in PARI/GP using the package [Apollonian](https://github.com/JamesRickards-Canada/Apollonian).

A summary of the data is found in the Excel file "Missing Curvatures".
Raw data files that are at most 25MB are found in the Data folder. The formatting of the files is:
* They are named "a_b_c_d_x-to-y_remqq.dat": the reduced Descartes quadruple is $[a, b, c, d]$ (the letter "m" denoting a minus sign), and we searched in the range from x to y for missing curvatures. We also only saved the missing curvatures that did not fall in one of the quadratic or quartic families described in the paper [The Local-Global Conjecture for Apollonian circle packings is false]()
* The first line of the file is the set of residue classes of curvatures modulo 24
* The second line is the vector of quadratic families that occur in the corresponding residue classes. An entry of $u$ means that any integer of the form $ux^2$ that lands in this residue class does not occur in the packing. Ensuring that we land in this residue class amounts to adding a coprimality condition to $x$ with a divisor of 6.
* The third line is the vector of quartic families that occur in the corresponding residue classes, with the same formatting as the quadratic families (except with $ux^4$ instead).
* The rest of the lines are the sets of missing curvatures that occur in the admissible residue classes, occuring in order. We have already removed the quadratic and quartic families from this data.

This data can easily be loaded into PARI/GP with the "readvec" command.

## Rough timings

The time taken to compute the missing curvatures (with the function "apol_missing") depends on the size of the circle packing, the bounds, and the hardware you are working on. To get a rough idea, the packing $[-11, 21, 24, 28]$ run on my laptop takes:
* $10^6$: 0s
* $10^7$: 0.328s
* $10^8$: 9.172s
* $10^9$: 7m 53.859s

Computations to $10^{10}$ typically finish in a few hours, and $10^{11}$ in half a day - several days. Another issue with increasing the bound is memory: up to $10^{11}$ requires around 4GB of memory, and $10^{12}$ is around 30GB. Computations to this range (and higher) would be doable with a large amount of memory (and a lot of time), or by breaking them into sequential computations on the various ranges. This would add quite a lot of computation time, but would require less memory. Since the main algorithm at hand is a depth first search, parallelization would improve timings.

All computations assume that the curvatures can fit into the C "long" data type. Therefore computations that approach this barrier ($\approx 1.84\cdot 10^{19}$ on a 64-bit machine) are not viable. However, they are unlikely to be viable anyway due to memory and time constraints.
