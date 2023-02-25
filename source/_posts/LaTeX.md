```yaml
title: LaTeX
date: 2022-10-17 23:11:01
tags:
 - LaTeX
```

# grammar

```latex
\section{Introduction}
\subsection{Template Styles}

\cite{lousurvey, zhong2021survey}

{\itshape scenario semantic}

\begin{itemize}[leftmargin=5.5mm]
\item xxx.
\end{itemize}

\begin{figure}[ht]
  \centering
  \includegraphics[width=\textwidth]{images/cla2.png}
  \caption{xxxx.}
  \Description{A woman and a girl in white dresses sit in an open car.}
  \label{fig:cla2}
\end{figure}

\begin{figure}[htbp]
\centering
\subfigure[pic1.]{
    \begin{minipage}[t]{0.25\linewidth}
    \centering
    \includegraphics[width=1in]{images/cla2.png}
    \end{minipage}
}

\subfigure[pic2.]{
    \begin{minipage}[t]{0.25\linewidth}
    \centering
    \includegraphics[width=1in]{images/cla117.png}
    \end{minipage}
}
\caption{Similar scenarios in an image, like (a). In each scenario, NPC1 starts from the left top, NPC2 starts from the left bottom, and ego starts from the right bottom.}
\Description{My classes.}
\label{fig:cla2}
\end{figure}

Fig. \ref{fig:cla2}

\label{tab:freq}
\ref{tab:freq}

\url{https://goo.gl/VLCRBB}

\verb|acmart|
\begin{verbatim}
  \documentclass[STYLE]{acmart}
\end{verbatim}

\begin{description}
  \item[\texttt{sidebar}:]  Place formatted text in the margin.
\end{description}

\texttt{acmsmall}

{\bfseries Your document will be returned to you for revision if
  modifications are discovered.}

\textbf{math}

\makecell[c]{Semi-Supervised \\ Learning}

% for special characters
\&
\O
{\char'134}
$\pi$
$\Psi$
$\alpha$
$\omega$
\lim_{n\rightarrow \infty}x=0
\sum_{i=0}^{\infty}x_i=\int_{0}^{\pi+2} f

% “”
`` ''
% ...
\texttt{$\,\ldots$}
```

[Title Capitalization Tool - Capitalize My Title - Title Case Tool](https://capitalizemytitle.com/) 

[Computing Classification System](https://dl.acm.org/ccs/ccs.cfm)

document class includes package

[Latex 数学符号 汇总 - ZingLix Blog](https://zinglix.xyz/2017/08/23/latex-maths-cheatsheet/)

# Format

```latex
% 1. at first, the preamble
\documentclass[sigconf]{acmart}
\usepackage{enumitem}
\usepackage{subfigure}

%% \BibTeX command to typeset BibTeX logo in the docs
\AtBeginDocument{%
  \providecommand\BibTeX{{%
    Bib\TeX}}}

% 2. start of the document
\begin{document}

%% The "title" command has an optional parameter,
%% allowing the author to define a "short title" to be used in page headers.
\title{xxx}
% \title[short title]{full title}

\author{Ben Trovato}
\authornote{Both authors contributed equally to this research.}
\email{trovato@corporation.com}
\orcid{1234-5678-9012}
\author{G.K.M. Tobin}
\authornotemark[1]
\email{webmaster@marysville-ohio.com}
\affiliation{%
  \institution{Institute for Clarity in Documentation}
  \streetaddress{P.O. Box 1212}
  \city{Dublin}
  \state{Ohio}
  \country{USA}
  \postcode{43017-6221}
}
\renewcommand{\shortauthors}{Trovato et al.}

\begin{abstract}
xxx
\end{abstract}

\keywords{datasets, neural networks, gaze detection, text tagging}

\maketitle

tttt
\end{document}

% 3. after last section of main body in document
\begin{acks}

\end{acks}

\balance
%% The next two lines define the bibliography style to be used, and
%% the bibliography file.
\bibliographystyle{ACM-Reference-Format}
\bibliography{documents/sample-base}

%% If your work has an appendix, this is the place to put it.
\appendix


% 4. main body in document
```
