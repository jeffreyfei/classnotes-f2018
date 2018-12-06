# Finals Summary Notes

[Midterm Summary Notes](/se-380/midterm-summary-notes.md)

- A system is stable if it goes to zero as time goes to infinity

- A negative pole will bring stability as the inverse laplace of $$\frac{1}{s+a}$$ is $$e^{-at}$$

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

![](/assets/Screenshot from 2018-12-05 21-38-42.png)