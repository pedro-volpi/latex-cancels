# cancels.sty (Extended Version)

This is an extended version of the `cancel.sty` package, primarily intended for use in math animations (like those created with Manim). It provides commands to draw various cancellation marks—slashes, crosses, and 'cancelled-to' arrows—over mathematical expressions or text.

**Note:** This package requires the **`pgf`** package for some of the extended functionality.

## Commands

The package provides the following main commands:

| Command | Description | Mode |
| :--- | :--- | :--- |
| `\cancel{<expression>}` | Draws a **diagonal line (slash)** through the expression. | Math & Text |
| `\bcancel{<expression>}` | Draws a **backslash** through the expression. | Math & Text |
| `\xcancel{<expression>}` | Draws an **X** (slash + backslash) through the expression. | Math & Text |
| `\cancelto{<value>}{<expr>}` | Draws a **diagonal arrow** through the expression, pointing *up and right* to `<value>`. (Original `cancelto`) | Math Only |
| `\dcancelto{<value>}{<expr>}` | Draws a **diagonal arrow** through the expression, pointing *down and right* to `<value>`. (Custom) | Math Only |
| `\lcancelto{<value>}{<expr>}` | Draws a **diagonal arrow** through the expression, pointing *up and left* to `<value>`. (Custom) | Math Only |
| `\dlcancelto{<value>}{<expr>}` | Draws a **diagonal arrow** through the expression, pointing *down and left* to `<value>`. (Custom) | Math Only |

## Package Options

Options are passed to the package when loading it (e.g., `\usepackage[makeroom]{cancel}`).

| Option | Description |
| :--- | :--- |
| `makeroom` | Increases the horizontal spacing around the cancelled expression to ensure the cancellation mark and value do not overlap neighboring content. |
| `overlap` | (Default) Does not affect horizontal spacing, allowing the marks to potentially overlap neighbors. |
| `thicklines` | Uses heavier lines for the cancellation marks and arrows. |
| `smaller` | (Default) Sets the cancellation value (`\cancelto` text) one size smaller than the current math style. |
| `Smaller` | Sets the cancellation value two sizes smaller than the current math style. |
| `samesize` | Sets the cancellation value to the same size as the current math style. |

## Customization

You can change the color of the cancellation marks by redefining `\CancelColor` (requires the `color` package):

```latex
\usepackage{color}
\renewcommand{\CancelColor}{\blue} % or \red, \green, etc.
```

## Installation
Place the `cancels.sty` file in your TEXMFHOME directory:

Find your personal TeX root: `kpsewhich --var-value=TEXMFHOME`

Create the structure inside it: `tex/latex/cancels/`

Place `cancels.sty` inside that folder.

# Tikz version

This package, a modern implementation of the original `cancel` package, uses **TikZ** to draw precise cancellation marks and arrows over mathematical expressions. This provides superior visual quality, color control, and flexibility, though it may be less compatible with external tools like Manim.

**Requirements:** This package requires the **`amsmath`** and **`tikz`** packages, including the `calc` and `arrows.meta` TikZ libraries.

### Commands

All commands are designed for use exclusively in **Math Mode** (`$...$`). They are generally used to show a value being cancelled and replaced by another value.

| Command | Syntax | Description | Output Direction |
| :--- | :--- | :--- | :--- |
| `\cancel{<expr>}` | `\cancel{x}` | Draws a simple diagonal **slash** through the expression. | N/A (Simple Slash) |
| `\cancelto{<value>}{<expr>}` | `\cancelto{5}{10}` | Draws an arrow pointing **up-right** through the expression, labeling the value at the top-right. | ↗️ |
| `\lcancelto{<value>}{<expr>}` | `\lcancelto{5}{10}` | Draws an arrow pointing **up-left** through the expression, labeling the value at the top-left. | ↖️ |
| `\dcancelto{<value>}{<expr>}` | `\dcancelto{5}{10}` | Draws an arrow pointing **down-right** through the expression, labeling the value at the bottom-right. | ↘️ |
| `\ldcancelto{<value>}{<expr>}` | `\ldcancelto{5}{10}` | Draws an arrow pointing **down-left** through the expression, labeling the value at the bottom-left. | ↙️ |

***

### Customization (TikZ Styles)

The appearance is controlled by TikZ styles. You can redefine these in your preamble using `\tikzset{...}` to customize the lines, arrows, and labels globally.

| TikZ Style Name | Default Definition | Controls |
| :--- | :--- | :--- |
| `cancel arrow` | `overlay, -{Stealth}, color=.` | The appearance of the cancellation arrow (line thickness, arrow tip, color). `color=.` matches the current text color. |
| `cancel label` | `overlay, inner sep=2.5pt, scale=0.55` | The appearance of the "to" value label (font size, inner padding). |
