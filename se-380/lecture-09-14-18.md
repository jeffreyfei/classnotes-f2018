## Linear Special Case

$$\frac{dx}{dt}=Ax(t)+Bu(t), A\in \mathbb{R}^{n\times n}, b\in\mathbb{R}^{n\times m},
C\in\mathbb{R}^{p\times n}$$

## Quadrator

$$m=4$$ (forces on rotors)
$$p=3$$ (position of UAV)
$$n=12$$ (position, orientation, velocity, angular velocity)

What is the state of a system? The state vector $$x(t_0)$$ encapsulates all of the system's dynamics up to time to specifically: For any two times $$t_0 < t_1$$, knowing $$x(t_0)$$ and knowing $$\{u(t):t_0\leq t \leq t_1\}$$ we can compute $$x(t_1)$$ and hence $$y(t_1)$$

### Ex 2.4.2

![](/assets/Screenshot from 2018-09-14 10-47-53.png)

- No applied force, no drag

$$M\ddot{y}=0$$

If we try a 1-dimensional state, say $$x:=y\in\mathbb{R}$$. In this case, knowing $$x(t_0)$$, without knowing $$\dot{y}(t_0)$$, we can't compute $$x(t_1)$$ for $$t_1>t_0$$. Same issue if we tried $$x:=\dot{y}\in R$$. Since the governing equation is 2nd order we need at least two initial conditions.

So $$x:=\begin{bmatrix}
y\\
\dot{y}
\end{bmatrix}
$$ is the natural choice


### Ex 2.5.1
![](/assets/Screenshot from 2018-09-14 10-53-36.png)

The model of this system is (see Ex. 2.3.3)

$$\ddot{\theta}=\frac{3}{M\ell^2}\tau-1.5\frac{g}{\ell}\sin{(\theta)}$$

To put tis system into state-> pace form 1, take

1. $$x=\begin{bmatrix}
\theta\\
\dot{\theta}
\end{bmatrix}
$$

2. $$u=\tau$$ (applied torque)
3. $$y=\theta$$ (position)

$$\dot{x}_1=x_2$$
$$\dot{x}_2=\frac{3}{M\ell^2}u-1.5 \frac{g}{\ell}\sin(x_1)$$
$$y=x_1$$

This is a nonlinear system so the model can't be written in the form $$\dot{x}=Ax+Bu, y=Cx+Du$$

### 2.4.5

![](/assets/Screenshot from 2018-09-14 11-00-24.png)

Choose

$$x_1 :=$$ voltage across capacitor $$=\frac{1}{C_0}\int^t_0y(\tau)d\tau$$

$$x_1 :=$$ current through inductor $$=y(t)$$

KVL

$$-u(t)+V_R(t)+V_C(t)+V_L(t)=0$$

$$\Rightarrow -u(t)+Rx_2(t)+x_1(t)+L \dot{x}_2(t)=0$$

Capactor dynamics: $$\frac{dx_1}{dt}=\frac{1}{C}x_2(t)$$

Combine equations

$$\dot{x}_1=\frac{1}{C}x_2$$
$$\dot{x}_2=\frac{-1}{L}x_1-\frac{R}{L}x_2+\frac{1}{L}u$$
$$y=x_2$$

State->Space Model
This is a linear system with

$$A=\begin{bmatrix}
0 & \frac{1}{C}\\
\frac{-1}{L} & \frac{R}{L}
\end{bmatrix},
B=\begin{bmatrix}
0\\
\frac{1}{L}
\end{bmatrix},
C=\begin{bmatrix}
0 & 1
\end{bmatrix},
D=0$$

## 2.5 Linearization

- In this course we will always linearize nonlinear models
- This refers to the process of *approximating* a nonlinear model with a linear model

## Ex. 2.5.2

Linearize

![](/assets/Screenshot from 2018-09-14 11-11-23.png)

$$y=x^3$$ at the point $$\bar{x}=1$$
$$\bar{y}=\bar{x}^3=1$$

Taylor series of $$f(x)=x^3$$ at $$\bar{x}$$ is

$$f(x)=\sum^{\infty}_{n=0}c_n(x-\bar{x})^n, c_n=\frac{1}{n!}\frac{d^nf}{dx^n}|_{x=\bar{x}}$$

$$=f(\bar{x})+\frac{df}{dx}|_{x=\bar{x}}(x-\bar{x})+$$ higher order terms

Keep only terms for $$n=0, 1$$

$$f(x)\approx f(\bar{x})+\frac{df}{dx}|_{x=\bar{x}}(x-\bar{x})$$

i.e.

$$y\approx\bar{y}+\frac{df}{dx}|_{x=\bar{x}}(x-\bar{x})$$

$$\Rightarrow y-\bar{y}\approx \frac{df}{dx}|_{x=\bar{x}}(x-\bar{x})$$

$$\Rightarrow dy=\frac{df}{dx}|_{x=\bar{x}}dx$$

In this example.

$$\delta y=3\delta x$$

### Ex. 2.5.3

$$y=\begin{bmatrix}
y_1\\
y_2
\end{bmatrix}
=
f(x)=
\begin{bmatrix}
x_1x_2-1\\
x_3^2-2x_1x_3
\end{bmatrix}=
\begin{bmatrix}
f_1(x)\\
f_2(x)
\end{bmatrix}$$