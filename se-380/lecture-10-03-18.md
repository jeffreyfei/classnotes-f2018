||BIBO Stable?|
|---|---|
|$$\frac{1}{s+1}$$|Y|
|$$\frac{1}{s}$$|N|
|$$\frac{1}{(s+3)^2}$$|Y|
|$$\frac{s+1}{(s+2)(s+3)}$$|Y|
|$$\frac{1}{s-1}$$|N|

- If $$G(s)$$ er, and not strictly proper,  then use long division to write
    $$G(s)=G_1(s)+const$$, $$G_1$$ strictly proper
    
- Impulse response is $$g(t)=g_1(t)+constant\cdot \delta(t)$$

- Theorem remains true with (ii), changed to $$g_1$$ absolutely integrable

e.g.

$$G(s)=\frac{(s+1)(s+2)}{(s+3)(s+4)}=\frac{-4s-10}{(s+3)(s+4)}+1$$


### Theorem 3.5.5
- If $$G(s)$$ is improper, then $$G$$ is *not* BIBO stable

##### Proof:

Write $$G(s)=\underbrace{G_1(s)}_{strictly~{}proper}+\underbrace{G_2(s)}_{polynomial~{}in~{}s}$$

So $$Y(s)=G_1(s)U(s)+G_2(s)U(s)$$

- If $$G_1$$ has poles with $$Re(s)\geq 0$$, then result follows from **Thm 3.5.4**
- If $$G_1$$ has all poles with negative real part, let $$u(t)=\sin(t^2)$$

- Any derivative of $$u$$ has polynomial terms in $$t$$ which are unbounded, e.g. $$\frac{du}{dt}=2t\cos(t^2)$$

    But $$y_2(t)=\mathcal L^{-1}(G_2(s)U(s))$$ is a linear combination of $$u$$ and its derivatives, so it is unbounded
    
    
## 3.5.1 Stability of State-space Models

$$\dot x=Ax+Bu$$
$$y=Cx+Du$$

##### ss2tf:

$$Y(s)=[C(sI-A)^{-1}B+D]U(s)$$
$$=[C\frac{\overbrace{adj(sI-A)}^{nxn~{}matrix}}{\underbrace{\det(sI-A)}}_{nth~{}order~{}polynomial}B+D]U(s)$$

eigenvalues of $$A=$$ roots of $$\det(sI-A)\supseteq$$ poles of TF

asymptotic stability $$\Rightarrow$$ BIBO staibility


### Ex. 3.5.5 (Mass spring)

$$\dot x=\begin{bmatrix}
0 & 1\\
-4 & 0
\end{bmatrix}+
\begin{bmatrix}
0\\
u
\end{bmatrix}u
$$

$$y=\begin{bmatrix}1&0\end{bmatrix}x$$

eigs of $$A=\pm j2\Rightarrow$$ Not A.S.

$$\frac{Y(s)}{U(s)}=\begin{bmatrix}
1&0
\end{bmatrix}
\begin{bmatrix}
s&-1\\
4&s
\end{bmatrix}^{-1}
\begin{bmatrix}
0\\
1
\end{bmatrix}
$$
$$=\begin{bmatrix}
1&0
\end{bmatrix}
\frac{\begin{bmatrix}
s&1\\
-4&s
\end{bmatrix}}
{s^2+4}
\begin{bmatrix}
0\\
1
\end{bmatrix}
$$
$$=\frac{1}{s^2+4}$$

$$\Rightarrow$$ System is not BIBO stable

- In this example the polynomials

$$C~{}adj(sI-A)B=1$$ and $$\det(sI-A)=s^2+4$$

are coprime and so eigs of $$A=$$ poles of TF

### 3.6 Steady-state gain

![](/assets/Screenshot from 2018-10-03 11-10-38.png)
- The steady-state gain of $$G$$ is the ratio $$\frac{y_{ss}}{b}$$

### Theorem 3.6.1 (Final Value Theorem)

Let $$F(s)=\mathcal L\{f(t)\}$$ for a signal $$f(t)$$. Assume $$F$$ is rational

1. if $$F(s)$$ has all its poles with negative real part except for a single pole at $$s=0$$, then
    $$\lim_{t\rightarrow\infty}f(t)=\lim_{s\rightarrow 0} sF(s)$$ (*)
    
2. If $$F$$ has repated poles at $$s=0$$, then $$f(t)$$ doesn't converge

3. If $$F$$ has poles with $$Re(s)\geq 0$$, other than at $$s=0$$, then $$f(t)$$ doesn't converge

|$$f(t)$$|$$\lim_{t\rightarrow\infty} f(t)$$|$$F(s)$$|$$\lim_{s\rightarrow 0} sF(s)$$|(*) applies?|
|---|---|---|---|---|
|$$e^{-t}$$|0|$$\frac{1}{s+1}$$|0|Y|
|$$1(t)$$|1|$$\frac{1}{s}$$|1|Y|
|$$t$$|$$\infty$$|$$\frac{1}{s^2}$$|$$\infty$$|N|
|$$te^{-t}$$|0|$$\frac{1}{(s+1)^2}$$|0|Y|
|$$e^t$$|$$\infty$$|$$\frac{1}{s-1}$$|0|N|
|$$\cos(\omega t)$$|N/A|$$\frac{s}{s^2+\omega^2}$$|0|N|

- To apply (*), you have to check that $$sF(s)$$ has no bad poles