---
layout: default
title: Proposition 5.1
---

## Proposition 5.1

### Extended proof of Proposition 5.1 with \( m^* \)

We define $m^*$ to be the smallest value such that $m^* P_{\text{all}}$ is a p-variable, meaning that
\begin{equation*}
\mathbb{P}\left\{ m^* P_{\text{all}} \le \alpha \right\} \le \alpha.
\end{equation*}
We can rearrange this condition to be
\begin{equation*}
\mathbb{P}\left\{ P_{\text{all}} \le \frac{\alpha}{m^*} \right\} \le \alpha;
\end{equation*}
if we define $\epsilon = \alpha / m^*$, this becomes
\begin{equation*}
\mathbb{P}\left\{ P_{\text{all}} \le \epsilon \right\} \le m^* \epsilon,
\end{equation*}
or, equivalently,
\begin{equation*}
\mathbb{P}\left\{ P_{\text{all}} > \epsilon \right\} \ge 1 - m^* \epsilon.
\end{equation*}

Let $p_{\text{all}}(x, y)$ denote the function corresponding to $P_{\text{all}}$. Then the prediction set
\begin{equation*}
C^{\text{data-avg}}_{\alpha}(X_{n+1}) = \left\{ y \in \mathcal{Y} : p_{\text{all}}(X_{n+1}, y) > \alpha \right\}
\end{equation*}
satisfies the coverage guarantee
\begin{equation*}
\mathbb{P} \left\{ Y_{n+1} \in C^{\text{data-avg}}_{\alpha}(X_{n+1}) \right\} \ge 1 - m^* \alpha.
\end{equation*}

Note that other transformations of $P_{\text{all}}$ can also yield valid p-variables while preserving the relative weighting. For instance, if $P_{\text{all}}$ is shifted rather than scaled, then the condition
\begin{equation*}
\mathbb{P}\left\{ m' + P_{\text{all}} \le \alpha \right\} \le \alpha
\end{equation*}
leads to a coverage guarantee of $1 - (m' + \alpha)$. We focus on the scale correction factor $m^*$ because it aligns with the framework of \citet{vovk2020combining} and works well in practice.