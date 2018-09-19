## 2.8 Transfer Functions

![](/assets/Screenshot from 2018-09-19 10-44-48.png)

The transfer function (TF) of this sytem is the ratio $$\frac{Y(s)}{u(s)}$$ where all Laplace transform are taken with zero initial conditions

### Ex 2.8.3

Recall the mass-spring-damper

$$M\ddot q=u-Kq-c(\dot q)$$

If the damper is nonlinear, then this system doesn't have a TF. If $$c(\dot q)=b\dot q$$, $$b$$ a constant, then

$$s^2MQ(s)=U(s)KQ(s)-sbQ(s)$$

$$\Rightarrow \frac{Q(s)}{U(s)}=\frac{1}{s^2 M+bs+K}$$

### Other examples (Table 2.2 of Notes)

![](/assets/Screenshot from 2018-09-19 10-52-35.png)

#### Definition 2.8.1

A TF $$G(s)$$ is *rational* if

1. $$G(s)=\frac{bms^m+...+b_1 s + b_0}{s^n+a_{n-1}s^{n-1}+...+a_1s+a_0}, a_i, b_i\in \mathbb{R}$$

2. A rational $$G(s)$$ is *proper* if $$n\leq m$$
3. A rational $$G(s)$$ is *strictly proper* if $$n>m$$

#### Definition 2.8.2

A complex number $$p\in \mathbb{C}$$ is a *pole* of $$G$$ if $$\lim_{s\rightarrow p} G(s)=\infty$$

A complex number $$z\in \mathbb{C}$$ is a *zero* of $$G$$ if $$\lim_{s\rightarrow z}G(s)=0$$

### 2.8.1 Obtaining a TF from a State Model

Start with

$$\dot x=Ax+Bu$$
$$y=Cx+Du$$

$$x\in \mathbb{R}^n, u\in \mathbb{R}^m, y\in \mathbb{R}^P$$

Take LTs with zero initial coniditons

$$sX(s)=AX(s)+BU(s)$$
$$Y(s)=CX(s)+DU(s)$$

$$X(s)=\begin{bmatrix}
x_1(s)\\
...\\
x_n(s)
\end{bmatrix}
$$

$$(sI-A)X(s)=BU(s)$$
$$X(s)=(sI-A)^{-1}BU(s)$$
$$\Rightarrow Y(s)=[C(sI-A)^{-1}B+D]U(s)$$
- $$[C(sI-A)^{-1}B+D]$$ is the transfer function matrix $$p\times m$$

#### Remark 2.8.3
- The TF obtained form a s.s. model is always rational and proper

```
State-space model  ------ ss2tf -------> Rational proper TF

TF model ------- ? -------> State-space model
```

- Only if TF is rational and proper, never unique

![](/assets/Screenshot from 2018-09-19 11-12-44.png)

$$G(s)=C(sI-A)^{-1}B+D$$

### Ex. 2.8.6

Recall linearlized model of pendulum at upright position $$(\bar x, \bar u)=(\begin{bmatrix}\pi \\ 0\end{bmatrix}, 0)$$

$$
\dot \delta x=\begin{bmatrix}
0 & 1\\
\frac{1.5g}{\ell} & 0
\end{bmatrix}
\delta x+
\begin{bmatrix}
0\\
\frac{3}{M\ell^2}
\end{bmatrix} \delta u,
\delta y=\begin{bmatrix}
1 & 0
\end{bmatrix}
$$

so $$G(s)=C(sI-A)^{-1} B$$
$$=\begin{bmatrix}
1\\
0
\end{bmatrix}
\begin{bmatrix}
s & -1\\
-1.5g/\ell & s
\end{bmatrix}^{-1}
\begin{bmatrix}
0\\
\frac{3}{M\ell^2}
\end{bmatrix}
$$

$$(sI-A)^{-1}=\frac{adj(sI-A)}{det(sI-A)}$$

$$=\begin{bmatrix}
1 & 0
\end{bmatrix}
\frac{
\begin{bmatrix}
s & -1\\
-1.5g/\ell & s
\end{bmatrix}^{-1}
}{
s^2-\frac{1.5g}{\ell}
}
\begin{bmatrix}
0\\
\frac{3}{m\ell^2}
\end{bmatrix}$$