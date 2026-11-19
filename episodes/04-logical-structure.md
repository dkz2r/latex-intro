---
title: 'The Structure of a Document'
teaching: 15
exercises: 10
---

:::::::::::::::::::::::::::::::::::::: questions

- How are LaTeX documents structured?

::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::: objectives

- Identify the different kinds of section commands in LaTeX.
- Create a list within a LaTeX document.

::::::::::::::::::::::::::::::::::::::::::::::::

## Sections

In a word processor, you might use headings to organize your document.In LaTeX, we'll use the
section commands:

- `\section{...}`
- `\subsection{...}`

LaTeX will handle all of the numbering, formatting, vertical spacing, fonts, and so on in order to
keep these elements consistent throughout your document. Let's add sections to our document.

```latex
\documentclass{article}

\begin{document}

	\section{Introduction}
	This is a collection of information about my favorite animals!

	\section{Habitats}
	Animals live in a variety of natural habitats.

	\subsection{Ocean}
	Mostly things with fins.

	\subsection{Arctic}
	Where it gets cold.

\end{document}
```

You should have something that looks like this:

![](fig/03-logical-structure/sections.PNG){alt='Our document with sections added.'}

::: callout

There are many different section commands in LaTeX, including `\subsubsection{...}`,
`\paragraph{...}`, `\chapter{...}`, and more. Each of these commands will create a new section
heading with a different level of indentation and numbering.

Some of these commands are only available in certain document classes, so be sure to check the
documentation for the class you are using.

:::

::: callout

There's also an alternative way to create sections in LaTeX using the `\section*{...}` command.
This command will create a section heading without numbering it. This can be useful for creating
unnumbered sections, such as an introduction or conclusion.

:::

## Table of Contents

We've seen how to make sections and how LaTeX will automatically number them for us. But we can
also use this feature to automatically generate a table of contents for our document! We can do
this by adding the `\tableofcontents` command to our document body. This will create a table of
contents at the location where the command is placed.

```latex
\documentclass{article}

\begin{document}

	\tableofcontents % The table of contents command has to go inside of the document environment

	\section{Introduction}
	This is a collection of information about my favorite animals!

	\section{Habitats}
	Animals live in a variety of natural habitats.

	\subsection{Ocean}
	Mostly things with fins.

	\subsection{Arctic}
	Where it gets cold.

\end{document}
```

![](fig/03-logical-structure/document-with-toc.png){alt='Our document with a table of contents.'}

## Document Classes

We've been including the `\documentclass{article}` at the top of our file each time, but what does this actually do?
A document class sets up the general layout of the document, including (but not limited to):

- design (margins, fonts, spacing, etc)
- availability of chapters
- title page layout

Document classes can also add new commands and environments to the document.

### Options for the Article Document Class

You might have noticed when we start typing `\documentclass` at the top of our file, the autocomplete has two options:

![The autocomplete options for `\documentclass`](fig/04-logical-structure/documentclass-typehint.png){alt='A screenshot of the typehint that appears for document class'}

We've just been using the first version, where we say "We want to use the article class", but the section version has a bit in square brackets that says "keyvals".
This is where we can specify basic options that apply to the entire document.
Let's update our document to use a slightly larger font size:

```latex
\documentclass[12pt]{article} % use the article class, and set the font to 12pt

\begin{document}

	\tableofcontents % The table of contents command has to go inside of the document environment

	\section{Introduction}
	This is a collection of information about my favorite animals!

	\section{Habitats}
	Animals live in a variety of natural habitats.

	\subsection{Ocean}
	Mostly things with fins.

	\subsection{Arctic}
	Where it gets cold.

\end{document}
```

Keep an eye on the preview when you hit "Build and View" - you should see the entire document re-render in a larger font.

We can specify additional options here by seperating them with a comma. Let's set the paper size:

```latex
\documentclass[12pt, a4paper]{article} % use the article class, and set the font to 12pt

\begin{document}

	\tableofcontents % The table of contents command has to go inside of the document environment

	\section{Introduction}
	This is a collection of information about my favorite animals!

	\section{Habitats}
	Animals live in a variety of natural habitats.

	\subsection{Ocean}
	Mostly things with fins.

	\subsection{Arctic}
	Where it gets cold.

\end{document}
```

::: callout

When setting up the LaTeX distribution, there is an option to set the default paper size to either A4 or Letter.
Since you never know who is going to be compiling your document, if you want to ensure that you get the same output no matter who opens it, it's a good idea to set at least the paper size here.

:::

### What does setting the Document Class do?

The document class also dictates what commands are available in the document.
Let's try setting our documentclass to "letter" and compile it to see what happens:

```latex
\documentclass[12pt, a4paper]{letter} % use the article class, and set the font to 12pt

\begin{document}

	\tableofcontents % The table of contents command has to go inside of the document environment

	\section{Introduction}
	This is a collection of information about my favorite animals!

	\section{Habitats}
	Animals live in a variety of natural habitats.

	\subsection{Ocean}
	Mostly things with fins.

	\subsection{Arctic}
	Where it gets cold.

\end{document}
```

Errors! You should have gotten an "Undefined Control Sequence" error for each `\tableofcontents`, `\section` and `\subsection` in your document.
This is because these commands aren't present in the letter document class.

We can modify our document to make it into a letter:

```latex
\documentclass{letter}

\address{Musterstraße 3 \\ 12543 Aachen}
\signature{Max Mustermann}

\begin{document}

	\begin{letter}{Prof. Joe Smith \\ Department of Zoology}

	\opening{Dear Sir or Madam,}
	This is a collection of information about my favorite animals!

	Animals live in a variety of natural habitats.

	\closing{Sincerely,}

	\end{letter}

\end{document}
```

So notice we now have a nested `\begin{letter}` environment.
We also have several commands like `\address`, `\signature`, `\opening` and `\closing`.
These commands are not available in the "article" class.

### Other Document Classes

In addition to "article" and "letter", base LaTeX also contains classes for "slides", "report" and "book".
These classes have been around for quite a long time, and are to modern eyes a little basic and lacking in features.
There are also the "KOMA scripts" - a collection of document classes that are more modern and feature rich than the basic classes.
We won't cover these here, but you can find [documentation for these online](https://ctan.org/pkg/koma-script).

## Challenges

::::::::::::::::::::::::::::::::::::: challenge

## Challenge 1: What needs to change?

:::::::::::::::::::::::: solution

## Answer


:::::::::::::::::::::::::::::::::
::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::: challenge

## Challenge 2: Can you do it?

:::::::::::::::::::::::: solution

## Answer


:::::::::::::::::::::::::::::::::
::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::: challenge


## Challenge 3: Enumerate your list manually

:::::::::::::::::::::::: solution

## Answer


:::::::::::::::::::::::::::::::::
::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::: keypoints

- LaTeX documents are structured using section commands.
- There are many different section commands in LaTeX, including `\subsubsection{...}`, `\paragraph{...}`, `\chapter{...}`, and more.
-

::::::::::::::::::::::::::::::::::::::::::::::::


::: spoiler

After this episode, [here is what our LaTeX document looks like](files/document_state/ep-03.tex).

:::
