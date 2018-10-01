### Theorem 3.1.2

The unique solution to $$\dot x=Ax$$, $$x(0)=x_0\in \mathbb R^n$$ is $$x(t)=e^{tA}x_0$$

Take LT of $$\dot x = Ax$$ without assuming $$x(0)=0$$

$$sX(s)-x+0=AX(s)$$

$$\Rightarrow X(s)=(sI-A)^{-1} x_0$$

$$\Rightarrow e^{tA}$$ and $$(sI-A)^{-1}$$ are LT pairs

### Mass-spring

![](/assets/Screenshot from 2018-10-01 10-56-52.png)
$$M\ddot q = u-kq$$

$$x:=\begin{bmatrix}
q\\
\dot q\end{bmatrix}
,y:=q$$

$$\dot x=\begin{bmatrix}
0 & 1\\
\frac{-K}{M} & 0
\end{bmatrix}+
\begin{bmatrix}
0\\
\frac{1}{M}
\end{bmatrix}
u
$$

$$y=\begin{bmatrix} 1&0\end{bmatrix}x$$

Find $$x(t) when k=4, M=1, u=0$$
$$x(0)=\begin{bmatrix}3 \\ 2\end{bmatrix}$$

$$sI-A=\begin{bmatrix}
s&-1\\
4& s\\
\end{bmatrix}
$$

$$(sI-A)^{-1}=\frac{
\begin{bmatrix}
s & 1\\
-4 & s
\end{bmatrix}
}{s^2+4}$$

use table to get $$\mathcal L^{-1}((sI-A)^{-1}))$$

$$e^{tA}=\begin{bmatrix}
\cos 2t & 1/2\sin{2t}\\
-2\sin{2t} & \cos{2t}
\end{bmatrix}
$$

$$x(t)=\begin{bmatrix}
3\cos{2t} + t\sin{2t}\\
-6\sin{2t} + t2\cos{2t}
\end{bmatrix}
$$

## 3.4 Stability of State-space Models

**Definition**:

The system $$\dot x=Ax$$ is *asymptotically stable* if $$x(t)\rightarrow 0$$ as $$t\rightarrow \infty$$ for any initial condition since $$x(t)=e^{tA}x_0$$, system is A.S. if and only if $$e^{tA}\rightarrow 0$$ as $$t\rightarrow \infty$$

### Prop 3.4.2

$$e^{tA}\rightarrow 0$$ as $$t\rightarrow \infty$$ if and only if every eigenvalue of A has negative real part

### Ex. 3.4.2

$$A=\begin{bmatrix}
0&1\\
-4&0
\end{bmatrix}
$$, $$e^{tA}$$ on board to right

So $$e^{tA}$$ does not go to zero as $$t\rightarrow \infty$$ so the system is not A.S.

**Check the proposition**

eigs of $$A=$$ roots of $$\det(sI-A)=$$ roots of $$s^2+4$$

$$\Rightarrow \sigma (A)=\{\pm j2\}\Rightarrow$$ by Prop, system is not A.S.

##### Revisit the mass damper example

Bring in friction: $$\ddot q=u-4q-\dot q$$
$$\Rightarrow$$ (Verify!)

$$A=\begin{bmatrix}
0 & 1\\
-4 & -1
\end{bmatrix}
$$

$$\det(sI-A)=\det\begin{bmatrix}
s& -1\\
4 & s+1
\end{bmatrix}=
s^2+s+4
$$

$$\sigma=\{\frac{-1\pm j\sqrt{15}}{2}\}\Rightarrow$$ System is A.S.

## 3.5 Bounded input Bounded Output Stability

$$Y(s)=G(s)U(s)$$ or $$y(t)=(g * u)(t)$$ (convolution)

#####Definition:

Real valued signal $$u(t)$$ is *bounded* if there exists $$a$$ constant $$b$$ such that, for all $$t\geq 0, |u(t)|\leq b$$

e.g. $$\sin t, \sin(t^2), 1(t), e^{-t}$$ (bounded)

$$e^{2t}, t\cos(t), t$$ (unbounded)

If $$u$$ is bounded, $$||u||_{\infty}$$ is its *least upper bound*

#####Definition:

An LTI system is *B.I.B.O stable* if every bounded input produces a bounded output

### Ex. 3.5.1

$$Y(s)=G(s)U(s), G(s)=\frac{1}{s+2}$$

Impulse response: $$\mathcal L(G(s))=e^{-2t}$$

$$y(t)=(g*u)(t), ||u||_{\infty}$$ assured finite

$$=\int^t_0 {e^{-2\tau}u(t-\tau)d\tau}$$

$$\leq\int^t_0 {e^{-2\tau}|u(t-\tau)|d\tau}$$

$$\leq\int^t_0 {e^{-2\tau} d\tau} ||u||_\infty$$

$$=\frac{1}{2}||u||_\infty$$

So,

$$||y||_\infty \leq \frac{1}{2}||u||_{\infty}$$

The system is BIBO stable

### Theorem 3.5.4

Assume $$G(s)$$, rational and strictly proper. The following are equivalent

1. System is BIBO stale

2. Impulse response $$G(t)=\mathcal L^{-1}(G(s))$$ is absolutely integrable $$\int^{\infty}_0 |g(t)|dt < \infty$$

3. Every pole of $$G$$ has negative real part
