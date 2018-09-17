### Ex. 2.5.3

$$y=f(x), f(x)=
\begin{bmatrix}
x_1x_2-1\\
x_3-2x_1x_3
\end{bmatrix}
,
\bar{x}=\begin{bmatrix}
1\\
-1\\
2
\end{bmatrix}
$$

Multivariable Taylor's

$$f(x)=f(\bar{x})+\frac{\partial f}{\partial x} |_{x=\bar{x}}(x-\bar{x})$$

where $$\frac{\partial f}{\partial x} |_{x=\bar{x}}$$ = Jacobian of the function $$f$$ evaluated at $$\bar{x}$$

$$=\begin{bmatrix}
\frac{\partial f_1}{\partial x_1} & \frac{\partial f_1}{\partial x_2} & \frac{\partial f_1}{\partial x_3}\\
\frac{\partial f_2}{\partial x_1} & \frac{\partial f_2}{\partial x_2} & \frac{\partial f_2}{\partial x_3}
\end{bmatrix}_{x=\bar{x}}
$$

$$=\begin{bmatrix}
x_2 & x_1 & 0\\
-2x_3 & 0 & 2x_3-2x_1
\end{bmatrix}=
\begin{bmatrix}
-1 & 1 & 0\\
-4 & 0 & 2
\end{bmatrix}
$$

$$y-\bar{y}\approx \frac{\partial f}{\partial x}|_{x=\bar{x}}(x-\bar{x})$$

$$y-\bar{y} = \delta y$$

$$\frac{\partial f}{\partial x}|_{x=\bar{x}}=A$$

$$(x-\bar{x})=\delta x$$

$$\delta y = A\delta x$$ - Linear approx. near $$\bar{x}$$

##### By direct extension

$$f(x, u)\approx f(\bar{x},\bar{u})+\frac{\partial f}{\partial x}|_{x=\bar{x}, u=\bar{u}}(x-\bar{x})+\frac{\partial f}{\partial u}|_{x=\bar{x}, u=\bar{u}} (u-\bar{u})$$

near $$(\bar{x}, \bar{u})$$

Let's apply this to 
$$\bar{x}=f(x, u), y=h(x, u)$$ (*)

Definition:

A constant pair $$(\bar{x}, \bar{u}\in \mathbb{R}^n\times R^{m}$$ is an *equilibirum configuration* of (*) if

$$f(\bar{x}, \bar{u}=\begin{bmatrix}
0\\
0\\
0\\
...\\
0
\end{bmatrix}$$

### Ex. 2.5.4
![](/assets/Screenshot from 2018-09-17 11-08-45.png)
$$
\dot{x}=\begin{bmatrix}
x_2\\
\frac{3}{M\ell^2}-\frac{1.5g}{\ell}\sin(x_1)
\end{bmatrix}
$$

$$y=x_1$$


Find equilibrium configurations corresponding to the pendulum being upright

$$x_1$$ equals $$\pi$$ at the upright position. So we have to solve

$$
\begin{bmatrix}
x_2\\
\frac{3}{M\ell^2}-\frac{1.5g}{\ell}\sin(x_1)
\end{bmatrix}
=
\begin{bmatrix}
0\\
0
\end{bmatrix}
\Rightarrow
\bar{x}_2=0,\bar{u}=0$$

The equal config is

$$(\bar{x},\bar{u})=(\begin{bmatrix}
\pi\\
0
\end{bmatrix}, 0)$$

Assume the nonlinear state-space model has an equilibrium config $$(\bar{x},\bar{u})$$

$$f(x, u)=f(\bar{x}, \bar{u})+\frac{\partial f}{\partial x}|_{x=\bar{x},u=\bar{u}}+
\frac{\partial f}{\partial u}|_{x=\bar{x},u=\bar{u}}(u-\bar{u})+h.o.t$$

Consider system solution "near" $$(\bar{x}, \bar{u})$$

$$\delta x(t):=x(t)-\bar{x}$$
$$\delta u(t):=u(t)-\bar{u}$$

$$\delta \dot{x}=\dot{x}-0$$
$$=f(x, u)-0$$
$$\approx A\delta x-B\delta u$$
- Linearlized state equation

The output equation $$y=h(x, u)$$ is linearized in the same way

$$\delta y=\frac{\partial h}{\partial x}|_{x=\bar{x}, u=\bar{u}} (x-\bar{x})+
\delta y=\frac{\partial h}{\partial x}|_{x=\bar{x}, u=\bar{u}} (u-\bar{u}),
\delta y(t)=y-h(\bar{x},\bar{u})$$

## Summary: Linearizing a  Nonlinear State-Space Model
$$\dot{x}=f(x, u), y=h(x, u)$$

1. Select a desired equilibrium configuration
    $$(\bar{x}, \bar u)$$, i.e., $$\bar x\in \mathbb R^n, \bar u\in \mathbb R^m$$ such that
    i) $$f(\bar x, \bar u)=0$$, ii) $$\bar y=h(\bar x,\bar u)$$  = desired output
2. Compute Jacobians A, B, C, D of $$f$$ and $$h$$ at $$(\bar x, \bar u)$$

3. The linearized system is:

$$\delta x= A\delta x + B\delta u$$
$$\delta y= C\delta x + D\delta u$$

### Ex. 2.5.5

$$d\dot x_1=x_2$$
$$\dot x_2=\frac{3}{M\ell^2}u-\frac{1.5g}{\ell}\sin(x_1)$$
$$y=x_1$$

$$\delta \dot{x}=\dot{x}-0$$
1) The eq. config correspoinding to upright position from last example is

$$\bar x=\begin{bmatrix}
\pi\\
0
\end{bmatrix}, \bar u = 0$$

2)

$$A=\frac{\delta f}{\delta x}|_{x=\bar x, u=\bar u}=
\begin{bmatrix}
0 & 1\\
\frac{1.5g}{\ell^2}\cos(x_1) & 0
\end{bmatrix}=
\begin{bmatrix}
0 & 1\\
\frac{1.5g}{\ell} & 0
\end{bmatrix}$$


$$B=\frac{\delta f}{\delta u}|_{x=\bar x, u=\bar u}=
\begin{bmatrix}
0\\
\frac{3}{M\ell^2}
\end{bmatrix},
C=\frac{\partial h}{\partial x} |_{x=\bar{x}, u=\bar{u}}=[1, 0]
$$

$$D=\frac{\partial h}{\partial u}|_{x=\bar{x}, u=\bar{u}}=0$$

3) Linearized modle

$$\delta \dot x=\begin{bmatrix}
0 & 1\\
\frac{1+5g}{\ell} & 0
\end{bmatrix} dx +
\begin{bmatrix}
0\\
\frac{3}{M\ell^2}
\end{bmatrix}du
$$

$$\delta y=\begin{bmatrix}
1 & 0
\end{bmatrix}\delta x
+\begin{bmatrix}
0
\end{bmatrix} \delta u
$$

$$dx(t)=\begin{bmatrix}
x_1(t)\\
x_2(t)
\end{bmatrix}-
\begin{bmatrix}
\pi\\
0
\end{bmatrix}, du(t)=u(t)-0$$

Read Section 2.7