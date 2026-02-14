# environmentoptional

A LaTeX package for creating custom environments with a flexible number of optional and mandatory arguments.

## Overview

The `environmentoptional` package provides an alternative to LaTeX's standard `\newenvironment` command, allowing you to define environments with:
- A variable number of **optional arguments** 
- A variable number of **mandatory arguments** 
- Default values for optional arguments
- Support for up to 9 total arguments (optionals + mandatory)

This package is built on `xparse` and uses LaTeX3 (`expl3`) for robust implementation.

## Installation

Run `pdflatex environmentoptional.ins` to extract `environmentoptional.sty`.
Copy `environmentoptional.sty` to your LaTeX distribution's `texmf` directory or your local project directory.

To generate the documentation, run `pdflatex environmentoptional.dtx`.

## Usage

### Basic Command: `\newenvironmentoptionals`

```latex
\newenvironmentoptionals{name}[n_opt][n_mand]{begin code}{end code}
```

**Parameters:**
- `name`: The environment name
- `[n_opt]`: Number of optional arguments (default: 0)
- `[n_mand]`: Number of mandatory arguments (default: 0)
- `{begin code}`: Code executed at `\begin{name}...`
- `{end code}`: Code executed at `\end{name}`

### Basic Usage of Custom Environment

```latex
\beginoptionals{name}[opt1][opt2]...{mand1}{mand2}...
...environment content...
\endoptionals{name}
```

## Examples

See `test_environmentoptional.tex` for comprehensive examples.

## Author

Sergio Martinez-Losa

## License

Released under the LaTeX Project Public License v1.3c or later.
See http://www.latex-project.org/lppl.txt
