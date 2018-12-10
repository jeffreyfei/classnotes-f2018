# Finals Summary Notes

[Midterm Summary Notes](/se-380/midterm-summary-notes.md)

- A system is stable if it goes to zero as time goes to infinity

- A negative pole will bring stability as the inverse laplace of $$\frac{1}{s+a}$$ is $$e^{-at}$$

### Error

$$E(s)=\frac{1}{1+C(s)P(s)} R(s)$$

### BIBO Stablility

- Every bounded input -> bounded out put

### Not BIBO stable

- Any bounded input -> unbounded output

### Internal Stability

- If every possible transfer function in the system is BIBO stable

### Input Output Stability

1. The transfer function $$1+PC$$ has no zeros in $$Re(s) > 0$$

2. The product has no unstable pole-zero cancellations

Internal stable $$\Rightarrow$$ Input output stable

### Closed-loop System Matrix

$$\dot x_{cl}=\begin{bmatrix}
\dot x_{p}\\
\dot x_c
\end{bmatrix}$$

![](/assets/Screenshot from 2018-12-05 21-38-42.png)

### Routh-Hurtwitz

- If polynomial is Hurwitz if all its roots lie in $$\mathbb C^-$$

- We can determine that a polynomial has a bad root if there exists a coefficient that has a different sign as the coefficient of $$s^n$$ (zero always counts as different sign)

##### Table construction
- First two rows comes from the polynomal (alternating pattern)

![](/assets/Screenshot from 2018-12-06 15-31-31.png)

### Root-locus

- The # of branches is the # of closed loop poles

Let $$n$$ be the finite poles and $$m$$ be the finite zeroes

![](/assets/Screenshot from 2018-12-07 07-34-59.png)

### Lead/Lag Controllers

Specs:
$$\Phi_{pm}$$, tracking => lead, lag

$$\Phi_{pm}, \omega_{gc}$$ => lead

### PID Controller

![](/assets/Screenshot from 2018-12-10 17-31-45.png)

![](/assets/Screenshot from 2018-12-10 17-31-57.png)

![](/assets/Screenshot from 2018-12-10 17-32-13.png)