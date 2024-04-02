# C++ Nauty and Traces Isomorphism Wrappers

## ...and an approximate isomorphism algorithm, `fake_iso`

## About

`Nauty` and `Traces` are graph isomorphism programs developed by Brendan McKay and Adolfo Piperno. A version of their code (27r4) is available directly in this repository.

The code in this repository offers `C++` wrappers around the `nauty` and `traces` `C` code. These wrappers are in no way affiliated with the official `nauty` or `traces` project(s). These wrappers provide the following:

 - A more convenient interface for `nauty` and `traces`' core features
 - The ability to call `nauty` and `traces` in multiple `C++` threads without errors
 - The ability to find the automorphism orbits of *edges*\*
 - The ability to conveniently manipulate graphs in `nauty` and `traces`' input format in amortized constant time, rather than needing to re-create the graph every time you want to modify it.
 - The ability to specify an initial *edge* coloring\*
 - The ability to run `traces` on directed graphs\*
 - A fast "fake" isomorphism algorithm that works on most graphs -- especially most graphs with varying node degrees

\* Not a feature of the original `nauty` and `traces` code

This code was originally developed for [the SCHENO project](https://github.com/schemanoise/SCHENO).

## Setup and Usage

To install, simply navigate to the `nt_wrappers` folder and run `setup.sh`

Then to check if it worked, you can try compiling the example tests with
`compile_nt_tests.sh`

See the PDF manual in the `documentation` folder for *many* more useful details and examples, as well as a discussion of the included fast "approximate" isomorphism algorithm, `fake_iso`.

See [the SCHENO project](https://github.com/schemanoise/SCHENO) for more involved examples of using this code.

## Potential Drawbacks and Limitations

Because this code was written with automorphism orbits of edges in mind, it supplies an augmented version of the original graph to the `nauty`/`traces` code.
If you don't care about the automorhism orbits of edges, you might find that this code runs slower and/or uses more RAM than a similar interface would if designed without the behind-the-scenes augmentation.

Due to the behind-the-scenes edge augmentation and `nauty`/`traces` original input size limits, the graph must obey the following size restrictions:

Let `n` be the number of nodes and `m` be the number of *undirected* edges\*\*.

 - Undirected Graphs: `1 <= n + m <= 2,000,000,000`
 - Directed Graphs:   `1 <= n + 2*m <= 2,000,000,000`

\*\*directed edge `(a, b)` and directed edge `(b, a)` count as the same undirected edge.

From the perspective of the user, the augmentation is completely invisible.

## License

This repository contains code from an external source with copyrights of its own. See `nt_wrappers/nauty27r4/COPYRIGHT` and `nt_wrappers/nauty27r4_modified/COPYRIGHT` for more details.

.

The rest of the code is licensed as follows:

Copyright (c) 2024 Justus Hibshman

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
