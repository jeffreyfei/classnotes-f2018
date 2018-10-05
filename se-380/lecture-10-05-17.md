### Theorem 3.6.2

If $$G$$ is BIBO stable and $$u(t)=b1(t)$$, then $$y_{ss}=b\cdot G(0)$$

#### Proof

If $$u(t)=b1(t)$$, then

$$y_{ss}=\int^\infty_0 g(\tau)u(t-\tau)d\tau=b\int^\infty_0g(\tau)d\tau=b\int^\infty_0 g(\tau)e^{-o\tau}d\tau$$


- Since $$G$$ is BIBO stable, all it's oles have neg real part so $$s=0$$ is in the R.O.C. of $$G(s)$$

So $$y_{ss}=b\dot G(0)$$

##### Conclusion

Steady-state gain $$\frac{y_{ss}}{b}=G(0)$$

#### Ex

$$\dot x=-2x+u$$
$$y=x$$
$$x\in \mathbb R$$

*Problem:* Given a constant reference $$r(t)=r_01(t)$$ for $$y$$, find a controller that makes $$y\rightarrow r$$ as $$t\rightarrow\infty$$

Try an open-loop configuration for now

$$Y(s)=\frac{1}{s+2} U(s)$$

```
            |-----------|       |-----------|
r(t) ------>|   C(s)    |------>|    P(s)   |------>y(t)
            |-----------|       |-----------|
```

Idea: Pick $$C$$ so that this system has s.s. gain of 1


$$Y(s)=\frac{1}{s+2} C(s)\frac{r_0}{s}$$

$$y_{ss}=\lim_{t\rightarrow\infty} y(t)=\lim_{s\rightarrow 0}s\frac{1}{s+2} C(s)\frac{r_0}{s}$$

- The above holds $$\Leftrightarrow C(s)$$ is BIBo stable
- In that case $$y_ss=\frac{1}{2}C(0)\cdot r_0$$

I'll pick $$C(s)=2=\frac{1}{P(0)}$$ (Pure gain)

$$C(s)=2\frac{3s+1}{4s+1}$$ also works


## 3.7 Frequency Response

$$Y(s)=G(s)(U(s)$$, $$G$$ BIBO stable

- If $$u(t)=\cos(\omega t), \omega\in \mathbb R$$, what is the steady-state output

![](/assets/Screenshot from 2018-10-05 11-03-46.png)

### Theorem 3.7.1

- The steady-state response $$u(t)=\cos(\omega t)$$ is $$y(t)=|G(j\omega)|\cos(\omega t+\angle G(j\omega))$$

#### Ex.

$$\dot x=-10x$$
$$y=x$$
$$x\in \mathbb{R}$$

$$\Rightarrow Y(s)=\frac{1}{s+1)}U(s)$$

Find s.s. output when $$u(t)=2\cos (3t+\frac{\pi}{6})$$

- System is BIBO stable so I can apply **Theorem 3.7.1**

$$y(t)=A\cos(3t+\frac{\pi}{6}+0)$$

$$A=|G(j3)|, 0=\angle G(j3)$$

$$G(j\omega)=\frac{1}{j\omega+10}\Rightarrow|G(j\omega)|_{\omega=3}=\frac{1}{\sqrt{9+100}}\approx 0.1$$

$$\angle G(j3)=\angle\frac{1}{j3+10}=\angle 1-\angle j3+10$$

$$=0-\angle j3+10=-\arctan2(10, 3)$$

$$\approx-0.2915~{}rad(\approx-16.7^{\circ})$$

### Definition 3.7.2

Assume $$G$$ is BIBO stable

1. The function $$\mathbb R\rightarrow \mathbb C, \omega \rightarrow G(j\omega)$$ is the *frequency response*

2. The function $$\mathbb R\rightarrow \mathbb R, \omega \rightarrow |G(j\omega)|$$ is the *magnitude response*

3. The function $$\mathbb R\rightarrow (-\pi, \pi], \omega\rightarrow\angle G(j\omega)$$ is the *phase response*

 
## 3.8 Graphical Representations of the Frequency Response

- When we graphically represent $$G(j\omega)$$, we'll only consider $$\omega\geq 0$$, since for rational TFs

$$|G(j\omega)|=|G(-j\omega)|$$, and $$\angle G(j\omega)=-\angle G(j\omega)$$

##### Two ways of graphical representation:

|Bode Plot|Polar  Plot|
|---|---|
|1. Magnitude plot|$$Re(G(j\omega))$$ vs $$Im(G(j\omega))$$ as functions of $$\omega$$|
|$$20\log |G(j\omega)|$$ vs. $$\log \omega$$||
|2. Phase plot||
|$$\angle G(j\omega)$$ vs $$\log\omega$$||
