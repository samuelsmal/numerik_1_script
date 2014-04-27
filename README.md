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

## Contribution
If you want to contribute: Please do!
But look at a the already written parts, to get a feeling for the style, 
used notation, etc.

I'll try to expand this file with notes.

Make sure to cut your lines at 80 characters, if it's a formula, algorithm, matlab code,.... Looks better, is easier to read, and people with smaller screensizes will thank you. But as always exceptions are ok. Normal text can easily be wrapped so just use your head.

Use `git-flow` and make small commits. Make sure to add yourself to the author
list in alphabetical order. And name them usefully, if you can, otherwise go nuts.

### Matrizes

To pretty print them use:

### A|b
```
\left(\begin{array}{r r | r}
	a_{11} & a_{12} & b_{1} \\
	a_{21} & a_{22} & b_{2}
\end{array}\right)
```

Which will give you:

```
/                 \
| a_11 a_12 | b_1 |
| a_21 a_22 | b_2 |
\                 /
```

### Normal matrices

Use the asterix (*) to denote alignment, use the option `r` to denote right 
alignemnt and wrap each number and operation:

```
\[\begin{matrix*}[r]
		I   &  2x_1 & + &   3x_2 & + &   4x_3 & + &  5x_4 & = &   5 \\
		II  &  6x_1 & + &  15x_2 & + &  19x_3 & + & 23x_4 & = &  30 \\
		III &  8x_1 & + &  42x_2 & + &  60x_3 & + & 70x_4 & = &  98 \\
		IV  & 12x_1 & + &  60x_2 & + &   1x_3 & + & 17x_4 & = & 144 \\
\end{matrix*}\]
```

### Algorithms

Adjust the following snippet to your use:

```
\begin{algorithm}
\caption{LU for band matrices}
\label{alg:lu-band-matrix} 
	\begin{algorithmic}
	    \ENSURE $a_{ij} = 0$, for $|i-j| > k$
	    \textbf{Input:} A (, k)
	    \textbf{Output:} L, U
	    \FOR{$m = 1 \dotsc d$} \STATE{
	    	$l_{mm} = 1$ \\
	    	$U_{mm} = a_{mm}$
	    	\FOR{$i = m + 1 \dotsc min(m + k, d)$} \STATE{
	    		$l_{im} = \frac{a_{im}}{U_{mm}}$ \\
	    		$U_{mi} = a_{ami}$
	    	}\ENDFOR
	    	\FOR{$i, j = m + 1 \dotsc min(m + k, d)$} \STATE{
	    		$a_{ij} = a_{ij} - l_{im}U_{mj}$
	    	}\ENDFOR
	    }\ENDFOR
	\end{algorithmic}
\end{algorithm}
```

For more information see the [manual](http://developer.berlios.de/docman/?group_id=3442).

### Matlab code

Adjust the following snippet to your use:

```
\begin{Matlab}
	[L, U, P] = lu(A)
\end{Matlab}
```

### Examples

For now please wrap each example in an the following way:

```
Example
	<Your stuff>
% END Example
```

I plan to create an environment - see Issue #3 - which would be basically the same as the one for the code:

```
\begin{Example}
	Consider ...
\end{Example}
```

### Special commands

A list of commands that could be usefull:

* `\BigO{<...>}` Prints a nice big-O-notation.

Append your own to the end of the style-file (`numerik1.sty`).

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
