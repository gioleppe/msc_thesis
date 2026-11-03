# MSc thesis scaffold

An English-language LaTeX starting point for a University of Pisa master's
thesis, adapted from the structure of the BSc thesis. The layout is not an
official university template: check your degree programme's requirements.

## Getting started

Edit the thesis details at the top of `main.tex`, then write the abstract and
chapters using the guidance comments in their files. Add references to `references.bib` and
cite them with `\cite{key}`. You can export BibTeX entries from a reference
manager and paste them into that file. Replace the example citation and
bibliography entry with sources relevant to your thesis. BibTeX needs at least
one citation to run successfully.

To add a chapter, create a `.tex` file containing `\chapter{Your title}` and
add `\input{your-file}` in `main.tex` where the chapter should appear. Add
figures with `\includegraphics{filename}` from `graphicx`; keep the image in
the project directory or specify its path relative to `main.tex`.

## Build

With MiKTeX, this one command runs pdfLaTeX and BibTeX as needed:

```text
texify --pdf --batch --synctex=1 --tex-option=-halt-on-error main.tex
```

In TeXstudio, open `main.tex` and set it as the master document. To make the
same build available from the editor, choose **User > User Commands > Edit
User Commands**, add a command, and set it to:

```text
texify --pdf --batch --synctex=1 --tex-option=-halt-on-error %.tex
```

Run it from **User > User Commands**, then open `main.pdf` in TeXstudio.
Chapter files include a root directive so they can be built from the editor.
Restart TeXstudio after installing MiKTeX if it cannot find `texify`.

Without MiKTeX's `texify`, run these commands from the project directory:

```text
pdflatex -interaction=nonstopmode -halt-on-error main.tex
bibtex main
pdflatex -interaction=nonstopmode -halt-on-error main.tex
pdflatex -interaction=nonstopmode -halt-on-error main.tex
```

The generated PDF and auxiliary build files are ignored by Git.
