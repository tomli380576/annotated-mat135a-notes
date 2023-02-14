## Feb 13 Final Example

Let the probability density function be:

$$
f(x) = \begin{cases}
1 &\text{if }x\in[0,1]\\
0 &\text{otherwise}
\end{cases}
$$

> **Question.** Find the expected value: $E[e^X]$

We first wrap $e^X$ with $Y = e^x$, then let:

$$
\begin{aligned}
F_Y(y) = P(Y = y) &= P(e^X\le y)\\
&= P(X\le \ln(y))\\
&= \int^{\ln(y)}_{-\infty} f(s)ds\\
&=\int^{\ln(y)}_0 ds\\
&=\ln(y)
\end{aligned}
$$

The probability density function can be found by taking the derivative:

$$
\begin{aligned}
f_Y(y) = F'_Y(y) = \frac 1y\hspace{2em}y\in[1,e]
\end{aligned}
$$

`@Hint` Since $x\in[0,1], y\in[e^0, e^1] = [1,e]$

Now we can compute the expectation:

$$
\begin{aligned}
E[Y] &= E[e^X]\\
&= \int^\infty_{-\infty} xf_Y(x)dx\\
&= \int^e_1x\frac 1x dx\\
&= e-1

\end{aligned}
$$
