### 4.3.3 Peak Time

- Smallest time $$T_p$$ such that $$||y||_\infty=y(T_p)$$
- Derived similarly to overshoot

$$T_p=\frac{\pi}{\omega_n\sqrt{1-z^2}}, 0<z<1$$

- $$T_p$$ only depends on the imaginary part of poles


Spec:$$T_p\leq T_p^{max}=3$$ seconds


$$\Rightarrow\omega_n\sqrt{1-z^2}\geq \frac{\pi}{T_p^{max}}$$

$$\Rightarrow\sqrt{\frac{K_{spring}}{M}-\frac{b^2}{4M^2}}\geq\frac{pi}{3}$$

**Summary** - underdamped 2nd order systems: poles

$$s=z\omega_n\pm j\omega_n\sqrt{1-z^2}$$

$$=\omega_n e^{\pm j(\pi-\theta)}$$
$$\theta=\arccos(z)$$


|   | 1  |  2 | 3  |  4 |
|---|---|---|---|---|
|$$\omega_n$$|+|+|no change|+|
|$$z$$|+|-|+|no change|
|$$\% OS$$|-|+|-|no change|
|$$T_s$$|-|no change|-|-|
|$$T_p$$|no change|-|+|-|



Read 4.4, 4.5

## Ch 3. Linear System Theory

$$\dot x=Ax+Bu$$
$$y=Cx+Du$$
or $$Y(s)=G(s)U(s)$$

### 3.1 Initial State Reponse
$$\dot x=Ax, x(0)=x_0\in \mathbb{R}^n, A\in \mathbb{R}^{n\times n}$$

#### Recall
- if $$n=1$$ (A is a scalar) the solution to this ODE is $$X(t)=e^{At}x_0$$
- $$e^{At}=1+tA+\frac{1^2}{2!}A^2+...$$

The motivates the definition of the *matrix exponential*

$$e^A:=I+A+\frac{1}{2!}A^2+...+=\sum^{\infty}{k=0}\frac{1}{K!}A^K$$

### Ex. 3.1.1

$$A=\begin{bmatrix}
0 & 0\\
0 & 0
\end{bmatrix}
\Rightarrow
e^{A}=\begin{bmatrix}
1 & 0\\
0 & 1
\end{bmatrix}$$

**Observe**

$$e^A$$ isn't the exponential of each term in $$A$$

### Ex. 3.1.2

$$A=\begin{bmatrix}
1 & 0\\
0 & 2
\end{bmatrix}
\Rightarrow
A^k=
\begin{bmatrix}
1^k & 0\\
0& 2^k
\end{bmatrix}
$$

$$e^A=I+\begin{bmatrix}
1 & 0\\
0 & 2
\end{bmatrix}
+
\frac{1}{2!}
\begin{bmatrix}
1^k& 0\\
0& 2^2
\end{bmatrix}
+...=\begin{bmatrix}
e^1 & 0\\
0 & e^2
\end{bmatrix}
$$

### Ex. 3.1.3

$$A=\begin{bmatrix}
0&1&0\\
0&0&1\\
0&0&0
\end{bmatrix}$$

Check that $$A^3=0$$