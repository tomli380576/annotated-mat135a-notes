# Feb 22. Notes

## Hazard Rate Function

Let $X$ be a continuous random variable and interpret $x$ as the ***lifetime*** of some item.

Let $f(x)$ be the probability density function of $x$ and let $F(x) = \int f$ be the cumulative density function. We can define:

## <span style="color: #ff6188">Def.</span> Hazard Rate / Failure Rate

$$
\lambda:[0, \infty) \to \R\\
\lambda (t) = \frac{f(t)}{1 - F(t)}
$$

## EX.1

Suppose an item has survived for some time $t$.

> **Question.** What's the probability that the item won't survive for an additional time $dt$?

This is given by the conditional probability:

$$
P(X\in (t, t + dt)\mid X > t)
$$

which expands to:

$$
\begin{aligned}
    &= \frac{P(X\in(t, t + dt)\cap X > t)}{P(X > t)}\\

    &= \frac{P( X \in(t, t + dt))}{P(X > t)}\\

    &\approx \frac{f(t)}{1 - F(t)}\cdot dt
\end{aligned}
$$

`@Hint` Use rectangle approximation for $P( X \in(t, t + dt))$ to get the final line.

## <span style="color: #8b74ff">Thm.</span> Hazard Rate of Exponential Random Variable is its parameter and is constant

Ley $X$ be an exponential random variable: $X\sim \text{Exponential}(\lambda_0)$

The hazard function for $X$ is:

$$
\lambda(t) = \frac{f(t)}{1-F(t)} = \frac{\lambda_0 e^{-\lambda_0t}}{e^{-\lambda_0t}} = \lambda_0
$$

`@Hint` The hazard rate for exponential random variables is constant.

## <span style="color: #8b74ff">Thm.</span> Hazard rate uniquely determines $F$

The hazard rate of a continuous random variable $X$ uniquely determines $X$'s cumulative density function $F_X(x)$.

### _Proof._

We need to show that there exists a relation between $\lambda(t)$ and $F_X(x)$.

Integrate $\lambda(t)$:

$$
\begin{aligned}
    \int^t_0\lambda(s) \text ds &= \int^t_0\frac{f(s)}{1-F(s)}\text ds\\
    & \small \text{use u-sub with } u = 1-F(s)\\
    &= -\ln(1-F(s))\;\Big|^t_0\\
    &= -\ln(1-F(t)) + \ln(1 - \underbrace{F(0)}_{0, \because \int^0_0 f = 0})\\
    &= -\ln(1- F(t)) + \ln(1)\\
    &=  -\ln(1- F(t))
\end{aligned}
$$

Isolate $F(t)$:

$$
\begin{aligned}
    \int^t_0\lambda(s) \text ds &= -\ln(1- F(t))\\
    \implies F(t)&=\boxed{ 1-\exp\left(-\int^t_0\lambda (s) \text ds\right)}
\end{aligned}
$$

Therefore we have a unique equality the connects $\lambda (s)$ and $F_X$

## EX.2

Let the death rate of a smoker ($S$) be twice of a non smoker($N$).

> **Question.** Compare the probability that an $A$ year old smoker will survive until age $B, B> A$ to that of a non-smoker.

We are given that a smoker is twice as likely to die as a non-smoker, so their respective hazard rates are:

$$
\lambda_S(t) = 2\lambda_N(t)
$$

We want to know:

$$
P(\text{Lifetime of $N$ is$>B$}\mid \text{Already $A$ years old})
$$

Expand with conditional probability:

$$
\frac{P(\text{Lifetime of $N$ is $ > B$}\cap\text{Lifetime of $N$ is $ > A$} )}{P(\text{Lifetime of $N$ is $ > A$})} \\
{}\\
= \frac{P(\text{Lifetime of $N$ is $ > B$})}{P(\text{Lifetime of $N$ is $ > A$})}
$$

The intersection can be simplified because the event $\text{Lifetime of N is > A}$ is a subset of $\text{Lifetime of N is > B}$ from the fact that $B > A$.

Apply <span style="color: #ff6188">Def.</span> Hazard Rate to both the numerator and the denominator:

$$
\begin{aligned}
    &\hspace{1em}\frac{P(\text{Lifetime of $N$ is $ > B$})}{P(\text{Lifetime of $N$ is $ > A$})}\\
    &= \frac{\lambda_N(B)}{\lambda_N(A)}\\
    &= \frac{\frac{f(B)}{1 - F(B)}\cdot dt}{\frac{f(A)}{1 - F(A)}\cdot dt}\\
    &\color{red}\small\text{Somehow get rid of $f(B)\cdot dt, f(A)\cdot dt$?}\\
    &= \frac{1-F(B)}{1-F(A)}\\
\end{aligned}
$$

Plug in the integrals found in <span style="color: #8b74ff">Thm.</span> Hazard rate uniquely determines $F$:

$$
\begin{aligned}
&= \frac{1-F(B)}{1- F(A)}\\
&= \frac{1 -  1+\exp\left(-\int^B_0\lambda_N (s) \text ds\right)}
{1 -  1+\exp\left(-\int^A_0\lambda_N (s) \text ds\right)}\\
&= \exp\left(-\int^B_A\lambda_N(s) \text ds\right)

\end{aligned}
$$

Similarly for smokers:

$$

\begin{aligned}

&\hspace{1em}P(\text{Lifetime of $S$ is$>B$}\mid \text{Already $A$ years old})\\

&= \exp(-\int^B_A\lambda_S(s)\text ds)\\

&= \exp\left(-\int^B_A2\lambda_N(s)ds\right)\\

&= \left(\exp(-\int^B_A\lambda_N(s)ds)\right)^2\\

\end{aligned}
$$

So we have this quadratic relationship.