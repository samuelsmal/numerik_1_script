# This is the collected script to the lecture Numerik 1, Spring Semester 2014, UZH

## Compilation

You can use the existing sublime-project-settings to compile with latexmk.
If you cannot use sublime text or don't want to you can use the following command:

```
latexmk -pdf -dvi- numerik1.tex
```

This will generate a pdf-file, while ommiting the dvi-file.

If you use another editor make sure to compile the `numerik1.tex`-file. 
Otherwise it will not work as desired.

## Contributation
If you want to contribute: Please do!
But look at a the already written parts, to get a feeling for the style, 
used notation, etc.

I'll try to expand this file with notes.

Make sure to cut your lines at 80 characters. Looks better, is easier to read, 
and people with smaller screensizes will thank you. But as always exceptions are
ok.

Use `git-flow` and make small commits. Make sure to add yourself to the author
list in alphabetical order. And name them usefully, if you can, otherwise go nuts.

### File structure

The style-file (`numerik1.sty`) can be found in the parent directory. 
Append and change it to your needs. But make sure not to brake existing 
code/format. Or make it clear that you intend to do so.

Since the lecture is - for now - quite hard to chapterize, 
just wrap one lecture in a chapter:

```
\chapter{Solutions of linear Systems, LU decomposition, Factorisation} % (fold)
\label{cha:solutions_of_linear_systems_lu_decomposition_factorisation}

Given a square matrix $\mathbf{A}$ of dimension $N \times N$ and a column vector 
$\mathbf{b} \in \mathbb{R}^N$, we want to solve $\mathbf{A}x = \mathbf{b}$.

...

% chapter solutions_of_linear_systems_lu_decomposition_factorisation (end)
```

Save the file in the `parts` directory and insert a 
`\input{./parts/solutions-of-linear-systems.tex}` at the right place in the 
`numerik1.tex` file.
