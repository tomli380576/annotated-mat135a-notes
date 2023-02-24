# Feb 17. Final Example

## <span style="color: #eeaa00">Prop.</span> Distribution of Distribution is Uniform

Let $X$ be a random variable with a cumulative density function $F_X$ where $F_X$ is both continuous and strictly increasing. 

Let $Y = F_X(x)$ , then $Y$ has a uniform distribution over $[0,1]$

##### *Proof.*

The cumulative density of $Y$ is:

$$
\begin{aligned}
F_Y(y) &= F_{F_X(x)}(y)\\
&= P(F_X(x)\le y)
\end{aligned}
$$

Recall that a strictly increasing function is injective. So $F_X^{-1}(x)$ exists.

Apply $F_X^{-1}$ to the inequality:

$$
\begin{aligned}
P(F_X(x)\le y) &= P\Big(F_X^{-1}(F_X(x))\le F_X^{-1}(y)\Big)\\
&= P(X \le F_X^{-1}(y))\\
&= \int^{F_X^{-1}(y)}_{-\infty}f_X(x)\,\text dx
\end{aligned}
$$

Now we use u-substitution to integrate this. 

$$
\frac{\text dF_X}{\text dx}=f_X\implies \text dF_X = f_X\text dx
$$

Substitute back in and change bounds of integration:

$$
\begin{aligned}
\int^{F_X^{-1}(y)}_{-\infty}f_X(x)\,\text dx 
&= \int^{F_X(F_X^{-1}(y))}_{-\infty} \text d F_X = \int^y_{-\infty}\text dF_X
\end{aligned}
$$

$F_X$ only ranges from $[0, 1]$, so we can replace the lower bound with 0.

$$
\int^y_{-\infty}\text dF_X = \int^y_{0}\text dF_X = y
$$

which is uniform over the interval $[0, 1]$.