# _map_align_
_map_align_ takes two contact maps and returns an alignment that attempts to maximize the number of overlapping contacts while minimizing the number of gaps.

![example image](https://raw.githubusercontent.com/sokrypton/map_align/master/map_align_fig.png)

### Installation
```sh
$ g++ -O3 -std=c++0x -o map_align main.cpp
```

### Usage
```
------------------------------------------------------
MAP_ALIGN
------------------------------------------------------
-a         contact map A            [REQUIRED]
-b         contact map B            [REQUIRED]
-gap_o     gap opening penalty      [Default=-1]
-gap_e     gap extension penalty    [Default=-0.01]
-ss_cut    seq seperation cutoff    [Default=3]
-iter      number of iterations     [Default=20]
-silent
------------------------------------------------------
Experimental features
------------------------------------------------------
-prf       add sequence profile
-prf_w     profile weight (if used) [Default=1]
------------------------------------------------------
```
```sh
$ map_align -a A.map -b B.map
```

### contact map format
- ```LEN 440``` - [len]gth
- ```CON 0 4 1.0```  - [con]tact, i, j and weight.
- ```PRF 0 A H 0.01 ... 0.01``` (optional) profile, i, amino acid (AA), secondary structure (SS) and profile frequencies (20 values). The order of the frequencies does not matter, as long as they match between the two contact maps being compared. The SS is not currently used in map_align and can be "X".
