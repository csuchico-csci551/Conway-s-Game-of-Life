# Conway's Game of Life

The Game of Life, also known simply as Life, is a cellular automaton devised by the British mathematician John Horton Conway in 1970. [1]

## The Rules

### For a space that is 'populated':
* Each cell with one or no neighbors dies, as if by solitude.
* Each cell with four or more neighbors dies, as if by overpopulation.
* Each cell with two or three neighbors survives.
### For a space that is 'empty' or 'unpopulated'
* Each cell with three neighbors becomes populated.

## Assignment

1. Implement 2 different Game of Life implementations in MPI using different approaches to slicing (Row, block, cell, etc).
2. Run benchmarks comparing your 2 different implementations.
    * Benchmarks should account for variability between runs, especially in a shared computing environment like the lab machines
    * Benchmarks should allow you to draw conclusions on how well your code can scale as the size of the board increases. 

### Input/Output Specifications

I will expect your code to take in 1 commandline argument, that will be the path to an input file, which will have the following form:

```
N G O
NxN grid
```

* **N** - the size of the NxN grid of *0*s and *1*s
* **G** - the number of generations to iterate through
* **O** - the output generation value. You should write the output after each O generations has passed. 

As an example small input file:

```
8 800 1
00000000
00000000
00000000
00010000
00001000
00111000
00000000
00000000
```

This input file is 8x8, should run through 800 generations, and output the state of the grid after each generation is calculated. In this example it would be expected you have 800 generation states all written to your output file. If we had the same input file but we only ran through 2 generations so *8 2 1* for the first line instead of the current *8 800 1* we would expect the following output in our *output.txt* file:

```
Generation 1:
00000000
00000000
00000000
00000000
00101000
00011000
00010000
00000000
Generation 2:
00000000
00000000
00000000
00000000
00001000
00101000
00011000
00000000
```

### Error Checking

* You need to validate that the number of processors your code is being run with evenly divides the N or size of your grid. 
* You can expect any inputs I give you will be properly formatted/structured; however, best practices would be to validate the input is structured correctly.

### Language Requirements

* You should not be using RAJA or OpenMP for this assignment
* You can use Python3, or C/C++
  * I still haven't determined what currently runs on the department's lab machines that you can use for initial testing of your code. I'm going to attempt to get Rust/Cargo installed so that's an option too. So this may change. I will be validating your assignment on the lab machines. 
  * If you use Python3 you need to provide a complete requirements.txt file so I can setup a virtualenv for your submission against what you expect it to have. 
  * If you use C or C++, you should include in your submission a Makefile that works on the lab machines to compile each of your variations accordingly. 
  * You should not intermix languages as your comparisons won't be tied to the MPI communications and slicing differences only. 

## Submission

You need to submit the following in a *tar.gz* to Tyson's Turnin System:

* Source code for both implementations along with any files needed to run/make your source code
  * It's possible you might want to include Readme in addition to these files just in case you're worried about me compiling running it after submission. 
* Lab report with the following:
  * Well formatted, I would highly recommend potentially learning LaTeX and structuring your assignment report like an [IEEE](https://www.ieee.org/content/dam/ieee-org/ieee/web/org/conferences/Conference-LaTeX-template_7-9-18.zip) or [ACM](https://www.acm.org/binaries/content/assets/publications/consolidated-tex-template/acmart-master.zip) conference publication. 
  * How you went about timing your code runs
    * What tool did you use?
    * Why did you use this approach/tool?
    * Are there limitations? 
    * How many runs did you do? 
    * Why did you choose that many runs? 
  * What size grids did you test
    * Why did you test those grid sizes?
    * How many processors did you use as the grid size increased? 
  * How well do each of your implementations scale? 
  * Is there anything else you feel you answered?
  * What new questions did this create for you?
  * Where did you do your testing? 
    * I recommend you do your final testing on a Google HPC instance; however, if you do this somewhere else you need to account for that in your report
    * What kind of system/architecture does your cluster have (processor type, cores per node, etc)
    
  
## Evaluation

Your assignment will be evaluated in the following fashion:

* 40 - correct implementaiton of game of life for 2 different slicing implementations
* 30 - timing data/methodology 
* 30 - conclusions/questions drawn from testing

## Extra Credit

For an extra 10 points of EC on this assignment. So not sure I'll be able to get the environment onto the lab machines; however, if it's possible reimplement your code in Rust and include the Rust implementations in your comparisons. How does Rust compare to your original implementations in scalability/speed/etc?

Make sure to include your source, Cargo.toml, and any other details/files along with your source to compile/run your Rust implementation.



[1]: https://web.archive.org/web/20090603015231/http://ddi.cs.uni-potsdam.de/HyFISCH/Produzieren/lis_projekt/proj_gamelife/ConwayScientificAmerican.htm
