# Feb 15. Notes

### <span style="color: #8b74ff">Thm.</span> Fubini's Theorem

Let a region $R\sube \R^2$, function $f:R\to \R$ be a continuous function such that

$$
\iint _R |f| \text d x\text d y < \infty
$$

Then the integral of $f$ over $R$ is equal to the iterated integral:

$$
\iint_Rf(x,y)\text dx\text dy = \int^d_c\int^b_a f(x,y)\text dx\text dy
$$

### <span style="color: #6088ff">Lemma.</span> Expected value of non-negative random variable

For a non-negative random variable $Y$, the expected value is:

$$
E[Y]=\int^\infty_0 P(Y> y)\text dy
$$

##### <u>_Proof._</u>

Let $f_Y$ be the probability density of $Y$, by [<span style="color: #8b74ff">Thm.</span> Fubini's Theorem](#thm-fubinis-theorem):

$$
\int^\infty_0P(Y> y)\text dy
= \int^\infty_0\int^\infty_y f_Y(x)\text dx \text dy
=\int^\infty_0\int^{\red x}_0f_Y(x)\text dy \text dx
$$

- Fubini's theorem applies here because $f_Y$ is continuous and the integral $\int^\infty_{-\infty} f_Y(s)ds = 1 < \infty$ is finite.

Evaluate the iterated integral:

$$
\begin{aligned}
\int^\infty_0\int^{x}_0f_Y(x)\text dy \text dx
&=\int^\infty_0 \left(\int^x_0\text dy\right)f_Y(x)\text dx\\
&=
\int^\infty_0xf_Y(x)\text dx\\
&=E[Y]
\end{aligned}
$$

### <span style="color: #eeaa00">Prop.</span> Wrapped Expected Value

If $X$ is a continuous random variable with p.d.f $f(x)$, then for all real valued function $g:\R\to\R, g(x)>0,\forall x\in \R$, the expected value of $g(X)$ is:

$$
E[g(X)] = \int^\infty_{-\infty}g(x) f(x)\text dx
$$

##### <u>_Proof Sketch._</u>

Since $g > 0$ , [<span style="color: #6088ff">Lemma.</span> Expected value of non-negative random variable](#lemma-expected-value-of-non-negative-random-variable) applies here.

$$
\begin{aligned}
E[g(X)] &= \int^\infty_0P(g(X)> y)\text dy\\
&= \int^\infty_0\int^\infty_{\red{g(x) > y}} f(x)\text dx \text dy
\end{aligned}
$$

Apply [<span style="color: #8b74ff">Thm.</span> Fubini's Theorem](#thm-fubinis-theorem):

$$
\begin{aligned}
\int^\infty_0\int^\infty_{{g(x) > y}} f(x)\text dx \text dy &= \int^\infty_0\int^{g(x)}_0 f(x)\text dy \text dx
\end{aligned}
$$