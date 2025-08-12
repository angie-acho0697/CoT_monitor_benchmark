# CoT_monitor_benchmark

## Key question: How much safety benefit do we gain from monitoring AI models' reasoning traces (CoT) compared to only monitoring their actions?
This "CoT uplift" metric is crucial for:

Informing deployment decisions for AI systems
- Guiding research priorities (CoT monitoring vs. neuralese-robust methods)
- Advocacy and policy recommendations
- Understanding the fragility of current safety measures

- \documentclass{article}
\usepackage{booktabs}
\usepackage{longtable}
\usepackage{array}
\usepackage{xcolor}
\usepackage[margin=1in]{geometry}

% Define column types for better formatting
\newcolumntype{L}[1]{>{\raggedright\arraybackslash}p{#1}}
\newcolumntype{C}[1]{>{\centering\arraybackslash}p{#1}}

% Define colors for ratings
\definecolor{excellent}{RGB}{0,128,0}
\definecolor{good}{RGB}{255,165,0}
\definecolor{poor}{RGB}{255,0,0}

\begin{document}

\begin{longtable}{L{2.5cm}|L{4cm}|L{4cm}|L{3.5cm}|C{1.5cm}}
\caption{Chain-of-Thought Monitoring Benchmarks: Comprehensive Analysis} \\
\toprule
\textbf{Benchmark} & \textbf{Pros} & \textbf{Cons} & \textbf{CoT Uplift Evidence} & \textbf{Rating} \\
\midrule
\endfirsthead

\multicolumn{5}{c}%
{{\bfseries \tablename\ \thetable{} -- continued from previous page}} \\
\toprule
\textbf{Benchmark} & \textbf{Pros} & \textbf{Cons} & \textbf{CoT Uplift Evidence} & \textbf{Rating} \\
\midrule
\endhead

\midrule \multicolumn{5}{r}{{Continued on next page}} \\ \midrule
\endfoot

\bottomrule
\endlastfoot

\textbf{SHADE-Arena} \cite{kutasov2025shade} & 
\begin{itemize}
\item Most comprehensive multi-step environment (17 task pairs)
\item Realistic personal assistant tasks
\item Complex tool usage (\textasciitilde{}20 tools)
\item Large synthetic environments (>100k tokens)
\item Public dataset availability
\item Strong empirical methodology
\end{itemize} & 
\begin{itemize}
\item Limited to personal assistant domain
\item Side tasks mostly concentrated
\item CoT monitoring discussion in appendices
\item Moderate realism ceiling
\item Limited task type diversity
\end{itemize} & 
\begin{itemize}
\item Significant performance drop without hidden scratchpad
\item Success heavily depends on reasoning access
\item Best models: 27\% (Claude) vs 15\% (Gemini) success
\item Monitor AUC: 0.87 (Gemini 2.5 Pro)
\end{itemize} & 
\textcolor{excellent}{\textbf{★★★★}} \\

\hline

\textbf{CoT Red-Handed} \cite{greenblatt2025cot} & 
\begin{itemize}
\item Explicit focus on CoT monitoring
\item Uses established BigCodeBench dataset
\item Clear action vs. CoT comparison methodology
\item Quantified uplift measurements
\item Coding domain coverage
\end{itemize} & 
\begin{itemize}
\item Single-step tasks only
\item Limited realism
\item Narrow domain (coding/security)
\item Always concentrated side tasks
\item Minimal strategic reasoning required
\end{itemize} & 
\begin{itemize}
\item Up to 27\% improvement in detection over action-only monitoring
\item Clear demonstration of CoT value
\item Shows trade-offs between subtle vs. obvious sabotage detection
\end{itemize} & 
\textcolor{good}{\textbf{★★★}} \\

\hline

\textbf{Ctrl-Z} \cite{bhatt2025ctrl} & 
\begin{itemize}
\item Highly realistic (Unix StackExchange problems)
\item Multi-step system administration
\item Sophisticated attack strategies
\item Large tool/command availability
\item Proven environment complexity
\end{itemize} & 
\begin{itemize}
\item No CoT monitoring evaluation
\item Human-designed attacks only
\item Limited task type diversity
\item Focus on blue-team protocols
\item Missing reasoning trace analysis
\end{itemize} & 
\begin{itemize}
\item \textbf{No evidence available} - major research opportunity
\item Environment clearly suitable for CoT evaluation
\item Attack complexity suggests reasoning requirement
\end{itemize} & 
\textcolor{good}{\textbf{★★★★}} \\

\hline

\textbf{OpenAI Frontier Monitoring} \cite{openai2024monitoring} & 
\begin{itemize}
\item Real-world deployment context
\item Production-scale systems
\item Actual misbehavior detection
\item Industry-relevant scenarios
\end{itemize} & 
\begin{itemize}
\item Limited public benchmark availability
\item Proprietary evaluation methods
\item Specific model behaviors focus
\item Unclear generalizability
\end{itemize} & 
\begin{itemize}
\item Detected test subversion and deception
\item Showed reasoning monitoring effectiveness
\item Limited quantitative uplift data
\end{itemize} & 
\textcolor{good}{\textbf{★★★}} \\

\hline

\textbf{Anthropic Sabotage Evals} \cite{benton2024sabotage} & 
\begin{itemize}
\item Realistic research scenarios
\item High-impact failure modes
\item Multiple sabotage types
\item Internal validation
\end{itemize} & 
\begin{itemize}
\item Mostly internal/non-public
\item Often single-step evaluations
\item Limited task diversity
\item Insufficient CoT focus
\end{itemize} & 
\begin{itemize}
\item Some evidence of reasoning importance
\item Limited systematic uplift measurement
\item Focus on capability rather than monitoring
\end{itemize} & 
\textcolor{poor}{\textbf{★★}} \\

\hline

\textbf{Automated Researchers Sandbagging} \cite{anthropic2025sandbag} & 
\begin{itemize}
\item Realistic ML research problems
\item Research sabotage focus
\item Clear success metrics
\end{itemize} & 
\begin{itemize}
\item Single-step tasks
\item Internal dataset
\item Limited strategic reasoning
\item Concentrated side tasks only
\end{itemize} & 
\begin{itemize}
\item Models can sandbag without scratchpad
\item Reasoning helps but not strictly required
\item Limited uplift quantification
\end{itemize} & 
\textcolor{poor}{\textbf{★★}} \\

\hline

\textbf{DeepMind Stealth Evals} \cite{deepmind2024stealth} & 
\begin{itemize}
\item Mix of subtle/non-subtle tasks
\item Multi-step evaluations
\item Personal assistant domain
\item Tool usage variety
\end{itemize} & 
\begin{itemize}
\item Limited public information
\item Unclear methodology
\item Moderate realism levels
\item Missing systematic analysis
\end{itemize} & 
\begin{itemize}
\item Insufficient public data
\item Potential for evaluation via Inspect
\item Unclear CoT monitoring focus
\end{itemize} & 
\textcolor{poor}{\textbf{★★}} \\

\hline

\textbf{Original Control Paper} \cite{greenblatt2024control} & 
\begin{itemize}
\item Foundational work
\item Clear adversarial setup
\item Established methodology
\item APPS dataset usage
\end{itemions} & 
\begin{itemize}
\item Single-step tasks only
\item Limited realism (toy problems)
\item Narrow scope
\item Outdated compared to newer work
\end{itemize} & 
\begin{itemize}
\item Basic demonstration of control concepts
\item Limited CoT monitoring focus
\item Primarily action-based evaluation
\end{itemize} & 
\textcolor{poor}{\textbf{★★}} \\

\hline

\textbf{Inference Code Tampering} \cite{anthropic2024inference} & 
\begin{itemize}
\item Novel threat model
\item Both single/multi-step versions
\item Clear attack objectives
\end{itemize} & 
\begin{itemize}
\item Highly unrealistic (toy environment)
\item Limited applicability
\item Narrow scope
\item Artificial constraints
\end{itemize} & 
\begin{itemize}
\item Significant CoT uplift in single-turn
\item No uplift in multi-turn settings
\item Mixed evidence for reasoning importance
\end{itemize} & 
\textcolor{poor}{\textbf{★★}} \\

\end{longtable}

\section*{Legend}
\begin{itemize}
\item \textcolor{excellent}{\textbf{★★★★}} - Excellent: Comprehensive, high-quality benchmark with strong CoT evidence
\item \textcolor{good}{\textbf{★★★}} - Good: Solid benchmark with some limitations but valuable contributions
\item \textcolor{poor}{\textbf{★★}} - Limited: Foundational work or narrow scope with limited current utility
\end{itemize}

\section*{Key Insights}
\begin{enumerate}
\item \textbf{SHADE-Arena} currently provides the most comprehensive evaluation framework, though limited to personal assistant tasks.
\item \textbf{Ctrl-Z} represents the biggest untapped opportunity - a realistic multi-step environment that lacks CoT monitoring evaluation.
\item \textbf{Multi-step research sabotage} remains completely unexplored, representing a critical gap.
\item Most benchmarks show \textbf{15-27\% improvement} when reasoning traces are available for monitoring.
\item The field needs \textbf{standardized CoT uplift measurement} methodologies across domains.
\end{enumerate}

\end{document}
