# Apollonian-Missing-Curvatures

This repository stores data related to curvatures that are admissible in a primitive Apollonian circle packing, but do not appear. Some of this data appears in the paper [The Local-Global Conjecture for Apollonian circle packings is false](). It was computed in PARI/GP using the package [Apollonian](https://github.com/JamesRickards-Canada/Apollonian).

A summary of the data is found in the Excel file "Missing Curvatures".
Raw data files that are at most 25MB are found in the Data folder. The formatting of the files is:
* They are named "a_b_c_d_x-to-y_remqq": the reduced Descartes quadruple is [a, b, c, d] (the letter "m" denoting a minus sign), and we searched in the range from x to y for missing curvatures. We also only saved the missing curvatures that did not fall in one of the quadratic or quartic families, as described in the paper [The Local-Global Conjecture for Apollonian circle packings is false]()
* The first line of the file is the set of residue classes of curvatures modulo 24
* The second line is the vector of quadratic families that occur in the corresponding residue classes. An entry of u means that any integer of the form ux^2 that lands in this residue class does not occur in the packing. Ensuring that we land in this residue class amounts to adding a gcd condition to n with a divisor of 6.
* The third line is the vector of quartic families that occur in the corresponding residue classes, with the same formatting as the quadratic families (except with ux^4 instead).
* The rest of the lines are the sets of missing curvatures that occur in the admissible residue classes, occuring in order. We have already removed the quadratic and quartic families from this data.

This data can easily be loaded into PARI/GP with the "readvec" command.
