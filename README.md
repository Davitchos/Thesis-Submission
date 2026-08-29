\documentclass[12pt]{article}
\usepackage{amsmath}
\usepackage{amsfonts}
\usepackage{dsfont}
\usepackage{amssymb}
\usepackage{bbm}
\usepackage{graphicx}
\usepackage[hidelinks]{hyperref}
\usepackage{enumitem}
\usepackage{geometry}
\usepackage{tabularx}
\usepackage{pifont}
\usepackage{makecell}
\usepackage{booktabs}
\usepackage{tabularx}
\usepackage{array}
\newcommand{\cmark}{\ding{51}} % check
\newcommand{\xmark}{\ding{55}} % cross
\usepackage[
  backend=biber,
  style=authoryear,
  doi=true,
  url=true,
  isbn=false
]{biblatex}
\addbibresource{src.bib}

\geometry{a4paper, margin=1in}

\title{
\normalsize Code Submission Overview

\LARGE Multi-Agent Reinforcement Learning for Dynamic Pricing in Markets with Switching Costs \\[0.75em]
}
\author{Davit Aghajanyan }
\date{August 2026}

\begin{document}
\maketitle

The code necessary for the thesis is devided into two sections.
\begin{enumerate}
    \item \textbf{DRL Environment} The contributions to the DRL-Framework developed by the chair. This contains the environment, logging and reward-surface plotting. This part of the code was executed on a remote server due to the large computational requirements.
    \item \textbf{Data Analytics} This section contains the subsequent evaluation of the learning outcomes. This contains the figures, regressions and final aggregated results referenced in the thesis. This was executed locally with the data obtained during computation as CSVs, decoupled from the remote server logic.
\end{enumerate}

\section{DRL Environment}
While the whole repository is very large and contains other projects and legacy code, this document outlines the files relevant for grading.
\begin{itemize}
    \item \textbf{scripts/run\_experiments} This file coordinated all experiments. It initializes an environment based on an input-CSV and runs all necessary configurations on the necessary seeds. 
    \item \textbf{src/env/switching\_costs} This is the environment file that specifies the model from chapter 3. It inherits from the parent classes of the framework and the verifier class. The structure of this file followed previous work by the chair.
    \item \textbf{src/env/sc\_evaluator} This file decouples the evaluation logic from the environment and keeps track of all necessary metrics.
    \item \textbf{src/utils/reward\_surface\_diagnostic} This creates the plots used in chapter 6.2. It was necessary to run them on the server as the plotting function needs to access the learned policy of the neural network. 
\end{itemize}

Other minor changes in the framework were made. These are rather  technicalities (e.g. adjusting MultiAgentCoordinator to call the reward surfaces plotting function after learning) or relicts of debugging and exploration. Both are insignificant for grading.

\section{Data Analytics}
This section prepares the raw data obtained from the DRL environment for the thesis. For that, this repository consists of the raw CSV results from the learning and three notebooks for the evaluation of the raw results.
\begin{itemize}
    \item \textbf{stability\_analysis} CV calculation and outlier removal for chapter 6.1.
    \item \textbf{equilibrium\_analysis} Verifier results for chapter 6.2.
    \item \textbf{hypotheses\_analysis} Hypotheses evaluation for chapter 6.3 to 6.6.
\end{itemize}


\end{document}
