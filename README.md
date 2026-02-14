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

Copy `environmentoptional.sty` to your LaTeX distribution's `texmf` directory or your local project directory.

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

**Argument references:** Use `#1`, `#2`, etc. in begin/end code to reference arguments.

### Basic Usage of Custom Environment

```latex
\beginoptionals{name}[opt1][opt2]...{mand1}{mand2}...
...environment content...
\endoptionals{name}
```

## Examples

### Example 1: Environment with 1 optional and 1 mandatory argument

```latex
\newenvironmentoptionals{mybox}[1][1]{
  \fbox{
  Optional: #1, Mandatory: #2
}{ 
  \par}
}

\begin{mybox}[default]{default2}
  This is in a box
\end{mybox}
```

### Example 2: Environment with 2 optional and 2 mandatory arguments

```latex
\newenvironmentoptionals{highlightenv}[2][2]{
  \textbf{Opt1: #1, Opt2: #2}\\
  \textit{Mand1: #3, Mand2: #4}
}{
  \par
}

\begin{highlightenv}[custom1][custom2]{required1}{required2}
  Content here
\end{highlightenv}
```

### Example 3: Environment with many arguments

```latex
\newenvironmentoptionals{complexenv}[8][1]{
  Parameters: #1, #2, #3, #4, #5, #6, #7, #8, Mandatory: #9
}{
  \rule{\linewidth}{0.4pt}
}

\begin{complexenv}[A][B][C][D][E][F][G][H]{FINAL}
  Content
\end{complexenv}
```

## Constraints

- The total number of arguments (`n_opt + n_mand`) must not exceed 9
- Optional arguments must come before mandatory arguments
- Optional arguments are specified in square brackets: `[value]`
- Mandatory arguments are specified in curly braces: `{value}`
- Default values for optional arguments are specified in the package declaration using brackets after the optional count parameter

## Advanced Features

### Default Values for Optional Arguments

Specify default values for optional arguments using brackets in the package declaration:

```latex
\newenvironmentoptionals{custom}[3][default1][default2][default3]{
  #1, #2, #3
}{
  \par
}
```

If an optional argument is not provided, the default value is used.

## Error Handling

The package provides clear error messages for:
- Environment name mismatches between `\beginoptionals` and `\endoptionals`
- Too many total arguments (exceeding 9)

## Version History

- v1.14 (2026-02-13): Initial release

## Requirements

- LaTeX2e
- `xparse` package
- `expl3` (L3 kernel)

## License

[Specify your license here]

## Author

[Author name and contact information]

## Support

For bug reports, feature requests, or questions, please contact the maintainer or visit the package repository.

---

**Compatibility:** Works with all modern LaTeX distributions (TeX Live, MiKTeX, MacTeX)
