# sourcebox 📦

[![Build LaTeX document](https://github.com/firefly-cpp/sourcebox/actions/workflows/main.yml/badge.svg)](https://github.com/firefly-cpp/sourcebox/actions/workflows/main.yml)
![License: LPPL 1.3c](https://img.shields.io/badge/license-LPPL%201.3c-orange.svg)

**sourcebox** is a tiny LaTeX package for [beamer](https://ctan.org/pkg/beamer) that places a nicely styled attribution box on a slide - a rounded, shadowed pill pinned near the bottom edge, ideal for crediting the source of an image, chart, or quotation.

No more fiddling with `\begin{textblock*}` coordinates or hand-rolled `\colorbox` hacks on every slide: one command, done.

## Features

- ✅ One-line usage: `\source{...}` inside any frame
- 📍 Three positions: `left`, `center`, `right` (default), computed from the paper size, so it works with any aspect ratio
- 🎨 Sensible soft-gray default styling, fully customizable colors — globally or per box
- 🌍 Renewable prefix label ("Image source:", "Vir:", "Quelle:", …)
- 📐 Adjustable width, vertical position, and edge margin
- 🪶 Lightweight: depends only on `xcolor`, `textpos`, and `ifthen` (in every standard TeX distribution); works with pdfLaTeX, XeLaTeX, and LuaLaTeX

## Usage

```latex
\documentclass{beamer}
\usepackage{sourcebox}

\begin{document}
\begin{frame}{My slide}
  \includegraphics[width=0.7\textwidth]{figure.pdf}

  \source{\url{https://example.com}}          % bottom right (default)
  % \source[left]{\url{https://example.com}}   % bottom left
  % \source[center]{\url{https://example.com}} % bottom center
\end{frame}
\end{document}
```

For a one-off box with its own colors (text color, background color) without touching the global defaults:

```latex
\sourcestyled[center]{white}{blue!55!black}{\url{https://example.com}}
```

## Customization

| Command | Effect | Default |
|---|---|---|
| `\sourceboxcolors{<fg>}{<bg>}` | Default text/background colors | dark gray on light gray |
| `\renewcommand{\sourceboxprefix}{Source:~}` | Label shown before the source text | `Image source:~` |
| `\setlength{\sourceboxwidth}{6cm}` | Box width | `7cm` |
| `\setlength{\sourceboxvpos}{8.8cm}` | Vertical position from the top of the slide | `8.8cm` |
| `\setlength{\sourceboxmargin}{4mm}` | Horizontal gap between box and slide edge | `4mm` |

> **Tip:** the default vertical position is tuned for the standard 4:3 beamer paper (12.8 cm × 9.6 cm). For `aspectratio=169`, set `\setlength{\sourceboxvpos}{6.5cm}`.

## License

This package is distributed under the [LaTeX Project Public License 1.3c](LICENSE) or later, the standard license for LaTeX packages on CTAN.

The demo figure `figs/vprasaj.pdf` originates from the [firefly-cpp/figures](https://github.com/firefly-cpp/figures) repository and is covered by that repository's license.
