## Summary Lecture #2

- Web server example
- A general definition of control engineering and essential block diagram (see also Fig 1.9 for notes)
- Control cycle
- Design cycle

#### Ex 2.1.1

![](/assets/Screenshot from 2018-09-10 12-39-11.png)

$$q\in \mathbb{R}$$, position of mass
$$M$$, mass in Kg
$$u$$, applied force

$$q=0$$ at location where spring is unstretched / uncompressed


**Newton's 2nd law:** $$M\ddot{q} = Z$$ force acting on $$M$$

$$\ddot{q}:=\frac{d^2 q}{dt^2}$$

- Force due to spring (assume linear, i.e., Hooke's law)
- Force due to damper (possibly non-linear, models function) $$c(\dot{q})$$

### 2nd order Nonlinear ODE

![](/assets/Screenshot from 2018-09-12 10-52-04.png)

$$M\ddot{q}=u-Kq-c(\dot{q})$$

- If the damper is linear, i.e. $$c(\dot{q})=b\dot{q}$$, b a constant, then the ODE becomes linear

$$V_R=h(i_R), \mathbb{R}\rightarrow\mathbb{R}$$ possibly nonlinear

$$u(t)=$$applied voltage
$$y(t)=$$voltage across cap

##### Apply KVL

$$-u(t)+V_R(t)+y(t)=0$$

$$V_R=h(i), i(t)=C\frac{dy}{dt}$$

**1st order nonlinear ODE:** $$-u(t)+h(C\dot{y})+y(t)=0$$

- If the resistor are linear, i.e., $$h(i)=R_i, R>0$$ constant, then the circuit is linear

##### Comments:
- See section 2.3 of notes for a bunch of examples
- Expectation is that you can model very simple mechanical and electrical systems

### 2.4 State-space models

- State-space models are a way of expressing mathematical models in a standard form

#### Ex. 2.4.1

![](/assets/Screenshot from 2018-09-12 10-58-59.png)

Newton's 2nd law: $$M\ddot{y}=u-D(\dot{y})$$

We put this model into standard form by defining two so-called "state variables"

##### State of System

$$x_1(t):=y(t)$$ (position)
$$x_2(t):=\dot{y}(t)$$ (velocity)

So we can write the system as

**State equation:**
$$\dot{x}_1=x_2$$
$$\dot{x}_2=\frac{1}{M}u-\frac{D(x_2)}{M}$$
**Output equation:**
$$y=x_1$$

These equation have the form

$$\dot{x}=f(x, u)$$
$$y=h(x)$$

- Non linear state-space model

Where, in this example

$$x=\begin{bmatrix}
x_1\\
x_2
\end{bmatrix}
\in \mathbb{R}^2
,
f(x, u)=
\begin{bmatrix}
x_2\\
\frac{u}{M}-\frac{D(x_2)}{M}
\end{bmatrix}
,
h(x)=x_1
$$

The function $$f$$ is linear of $$D$$ is, $$h$$ is linear

**Special case**: Suppose the force due to air resistance where linear i.e. $$D(x_2)=dx_2$$, $$d$$ a constant

Then $$f$$ becomes linear and can be written as

$$f(x,u)=
\begin{bmatrix}
0 & 1\\
0 & \frac{-d}{M}
\end{bmatrix}
\begin{bmatrix}
x_1\\
x_2
\end{bmatrix}+
\begin{bmatrix}
0\\
\frac{1}{M}
\end{bmatrix}
u
$$

Let

$$A:=
\begin{bmatrix}
0 & 1\\
0 & \frac{-d}{M}
\end{bmatrix}
$$
and
$$B:=
\begin{bmatrix}
0\\
\frac{1}{M}
\end{bmatrix}
$$

and we get the linear special case

$$\dot{x}=Ax+By$$
$$y=Cx, C=[1, 0]$$

- Which is a state-space model of a LTI system

- Generalizing this example, we can say that an important *class of systems* have models of the form

$$\dot{x}=f(x, u), f:\mathbb{R}^n\times\mathbb{R}^m\rightarrow \mathbb{R}^n$$
$$y=h(x, u), h:\mathbb{R}^n\times\mathbb{R}^m\rightarrow \mathbb{R}^p$$

- The model is *nonlinear*. There are $$m$$ control inputs $$u=(u_1, ..., u_m)\in \mathbb{R}^m$$. There are $$p$$ outputs $$y=(y_1, ...,y_p)\in \mathbb{R}^p$$ and the state has dimension $$n, x=(x_1, ...,x_n)$$

e.g. previous example $$n=2, m=1, p=1$$

![](/assets/Screenshot from 2018-09-12 11-22-47.png)

$$u=
\begin{bmatrix}
u_1\\
u_2
\end{bmatrix}
\in \mathbb{R}^2,
y=
\begin{bmatrix}
y_1\\
y_2
\end{bmatrix}
\in \mathbb{R}^2

$$

$$m=2, p=2$$

$$x=
\begin{bmatrix}
x_1\\
x_2\\
x_3\\
x_4
\end{bmatrix}
=
\begin{bmatrix}
y_1\\
y_2\\
y_3\\
y_4
\end{bmatrix}
,
n=4
$$