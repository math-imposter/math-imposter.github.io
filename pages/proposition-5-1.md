---
layout: default
title: Proposition 5.1
---

## Proposition 5.1

### Extended proof of Proposition 5.1 with \( m^* \)

We define \( m^* \) to be the smallest value such that \( m^* P_{\text{all}} \) is a p-variable, meaning that:

$$
\mathbb{P}\left\{ m^* P_{\text{all}} \le \alpha \right\} \le \alpha.
$$

We can rearrange this condition to be:

$$
\mathbb{P}\left\{ P_{\text{all}} \le \frac{\alpha}{m^*} \right\} \le \alpha;
$$

If we define \( \epsilon = \alpha / m^* \), this becomes:

$$
\mathbb{P}\left\{ P_{\text{all}} \le \epsilon \right\} \le m^* \epsilon,
$$

or, equivalently:

$$
\mathbb{P}\left\{ P_{\text{all}} > \epsilon \right\} \ge 1 - m^* \epsilon.
$$

Let \( p_{\text{all}}(x, y) \) denote the function corresponding to \( P_{\text{all}} \). Then the prediction set:

$$
C^{\text{data-avg}}_{\alpha}(X_{n+1}) = \left\{ y \in \mathcal{Y} : p_{\text{all}}(X_{n+1}, y) > \alpha \right\}
$$

satisfies the coverage guarantee:

$$
\mathbb{P} \left\{ Y_{n+1} \in C^{\text{data-avg}}_{\alpha}(X_{n+1}) \right\} \ge 1 - m^* \alpha.
$$

Note that other transformations of \( P_{\text{all}} \) can also yield valid p-variables while preserving the relative weighting. For instance, if \( P_{\text{all}} \) is shifted rather than scaled, then the condition:

$$
\mathbb{P}\left\{ m' + P_{\text{all}} \le \alpha \right\} \le \alpha
$$

leads to a coverage guarantee of \( 1 - (m' + \alpha) \). We focus on the scale correction factor \( m^* \) because it aligns with the framework of [Vovk and Wang (2020)](https://proceedings.mlr.press/v108/vovk20a.html) and works well in practice.

### Finite-sample statement with \( \widehat{m}^* \)

We define \( \widehat{m}^* \) to be the smallest value such that \( \widehat{m}^* \widehat{P}_{\text{all}} \) is a p-variable, where \( \widehat{P}_{\text{all}} \) is the empirical random variable associated with \( \widehat{F}^{\text{cons}}_{P_{\text{all}}} \).

Let \( A \) be the event that \( \widehat{m} \widehat{P}_{\text{all}} \leq \widehat{m} \alpha \) and \( B \) be the event that \( \widehat{m} \alpha < s \). Then, using the inequality \( \mathbb{P}(A) \leq \mathbb{P}(A \cap B) + \mathbb{P}(B^c) \), we have:

$$
\mathbb{P}(\widehat{m} \widehat{P}_{\text{all}} \leq \widehat{m} \alpha) \leq \mathbb{P}(\widehat{m} \widehat{P}_{\text{all}} \leq s) + \mathbb{P}(\widehat{m} \alpha \geq s).
$$

By the definition of \( \widehat{m} \), the scaled variable \( \widehat{m} \widehat{P}_{\text{all}} \) is a p-variable, so it satisfies:

$$
\mathbb{P}(\widehat{m} \widehat{P}_{\text{all}} \leq \alpha) \leq \alpha.
$$

Markov's inequality tells us that:

$$
\mathbb{P}(\widehat{m} \alpha \geq s) = \mathbb{P}\left( \widehat{m} \geq \frac{s}{\alpha} \right) \leq \frac{\mathbb{E}[\widehat{m}]}{s / \alpha} = \frac{\alpha \mathbb{E}[\widehat{m}]}{s}.
$$

Combining these observations, we obtain:

$$
\mathbb{P}(\widehat{P}_{\text{all}} \leq \alpha) \leq s + \frac{\alpha \mathbb{E}[\widehat{m}]}{s},
$$

which holds for any \( s > 0 \).

We optimize by minimizing the right-hand side over \( s \). The minimum of \( s + \frac{c}{s} \) occurs at \( s = \sqrt{c} \), so we choose \( s = \sqrt{\alpha \mathbb{E}[\widehat{m}]} \), which gives the bound:

$$
\mathbb{P}(\widehat{P}_{\text{all}} \leq \alpha) \leq 2 \sqrt{ \alpha \mathbb{E}[\widehat{m}] },
$$

or equivalently:

$$
\mathbb{P}(\widehat{P}_{\text{all}} > \alpha) \geq 1 - 2 \sqrt{ \alpha \mathbb{E}[\widehat{m}] }.
$$

Let \( \widehat{p}_{\text{all}}(x, y) \) denote the function corresponding to \( \widehat{P}_{\text{all}} \). Then the prediction set:

$$
\widehat{C}^{\text{data-avg}}_{\alpha}(X_{n+1}) = \left\{ y \in \mathcal{Y} : \widehat{p}_{\text{all}}(X_{n+1}, y) > \alpha \right\}
$$

satisfies the coverage guarantee:

$$
\mathbb{P} \left\{ Y_{n+1} \in \widehat{C}^{\text{data-avg}}_{\alpha}(X_{n+1}) \right\} \ge 1 - 2 \sqrt{ \alpha \mathbb{E}[\widehat{m}] }.
$$
