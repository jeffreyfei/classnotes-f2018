#### Ex. Linearization

##### Consider

$$\dot x_1=\cos x_3+x_4$$

$$\dot x_2=x_4 \sin x_3$$

$$\dot x_3 = x_4^3 +1 $$

$$\dot x_4 = x_4 u$$

Linearize about $$\bar x=(0, 0, 0, -1)$$


#### Ex.

#### Linear System Theory

##### Time (T)

$$\dot x=Ax+Bu$$

$$y=Cx+Du$$


##### Frequency (F)

$$Y(s)=G(s)U(s), G(s)=C(sI-A)^{-1}B+D$$

##### Asymptotic

What:

If $$u=0$$, for any $$x(0)$$, $$\lim_{t\rightarrow\infty} x(t)=0$$

How to test:

- Eigenvalues of A

##### Recall:

$$\lambda$$ is an eigenvalue if there is some $$v$$

$$Av=\lambda v$$
$$\Leftrightarrow (\lambda I - A)v = 0$$
$$\Leftrightarrow \det (\lambda I-A)=0$$

if $$\dot x = Ax$$

$$x(t)=e^{tA} x(0)$$

$$e^{tA}=\ell^{-1}\{(sI-A)^{-1}\}$$

- Eigenvalues of A happens to be the poles of the laplace transform
    - Stable if the poles has negative real part
    
$$(sI-A)^{-1}=\begin{bmatrix}
s-1 & -1 & 0\\
+2 & s+2 & 0\\
0 & 0 & s
\end{bmatrix}$$

$$=\begin{bmatrix}

\frac{s+2}{s(s+1)} & \frac{1}{s(s+1)} & 0\\
\frac{-2}{s(s+1)} & \frac{s-1}{s(s+1)} & 0\\
0 & 0 & \frac{1}{s}

\end{bmatrix}$$

