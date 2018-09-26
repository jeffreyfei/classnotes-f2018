## 4.2.1 Underdamped Systems

$$(0 < z < 1)$$

Poles: $$s=-z\omega_n\pm j\omega_n\sqrt{1-z^2}$$

$$=\omega_n e^{\pm j(\pi-\theta)}, \theta=\arccos(z)$$

![](/assets/Screenshot from 2018-09-26 10-56-59.png)

**Zeroes**: None
**Steady-state gain:** $$G(0)=K$$
**Bandwidth**: $$\omega_{BW}\approx \omega_n$$ (but it depends on $$z$$)
**Impulse response**: $$g(t)=\mathcal L^{-1}(G(s))=k\frac{\omega_n}{\sqrt{1-z^2}}e^{-z\omega_n t} \sin(\omega_n\sqrt{1-z^2})t, t\geq 0$$

$$e^{z\omega_n t}$$ .+ decay rate depends on real part of poles


#### Observe

For fixed $$z$$, larger bandwidth $$(\omega_n) \Leftrightarrow$$ Faster decay

#### Step Response:

$$u(t)=1(t)\Rightarrow U(s)=\frac{1}{s}$$

$$Y(s)=G(s)U(s)\Rightarrow y(t)=\mathcal{L}^{-1}(G(s)\frac{1}{s})$$

$$=K(1-\frac{1}{\sqrt{1-z^2}} e^{-z\omega_n t}\sin (\omega_n\sqrt{1-z^2} t+\theta))$$


- See figures 4.9/4.10 in notes

#### Observations

- As $$z\rightarrow$$1, imaginary part of poles approach zero, response becomes less oscillatory, and there is less overshoot
- As $$z\rightarrow 0$$, real part of poles apporach zero, response is more oscillatory, more overshooot
- As bandwidth increases, respones gets faster
- Rate of decay depends on real part of poles
- Frey of oscillation depends on imaginary part of poles

## 4.3 General Characteristics of a Step Response

- Common metrics to quantify the quality of a step response
- Metrics apply to *any system*, not just 1st and 2nd order
- In this section we'll use an underdamped 2nd order system to express the metrics in terms of $$k, z, \omega_n$$
- Value of using the 2nd order TF is
    1. Easy
    2. We can approximate higher order systems using 2nd order models

![](/assets/Screenshot from 2018-09-26 11-05-30.png)

#### Figure 4.13

![](/assets/Screenshot from 2018-09-26 11-05-48.png)

## 4.3.1 Overshoot

$$\%OS:=\frac{||y||_\infty-|y_{s.s.}|}{|y_{s.s.}|}$$

for $$u(t)=1(t), y_{s.s.}=G(0)$$

- For an underdamped 2nd order system

$$\%OS=\exp(\frac{-z\pi}{\sqrt{1-z^2}}), 0 < z < 1$$

- Only depends on damping ratio, i.e., on the argument of poles

    More damping $$\Leftrightarrow$$ less overshoot
    $$z\rightarrow 1$$
    
    
### Ex (mass-spring-damper)

$$\frac{Y(s)}{U(s)}=\frac{1/M}{s^2+\frac{b}{M}s+\frac{K_{spring}}{M}}$$

Find conditions on $$b, M, K_{spring}$$ so that $$\% OS \leq \% OS^{max}=0.05$$

$$z=\frac{b}{2\sqrt{K_{spring} M}}, \% OS\geq \% OS^{max}\Leftrightarrow
z\geq \frac{-\ln(\%OS^{max})}{\sqrt{\pi^2+[\ln(\%OS^{max}]^2}}=: z_{min}$$

To meet spec, we need

$$\frac{b}{2\sqrt{K_{spring}M}}\geq 0.6901$$

- We can view this spec as a constraint on the pole angles

$$\theta=\arccos z$$, so $$z\geq z_{min}\Leftrightarrow \theta \leq \arccos(z_{min})$$

![](/assets/Screenshot from 2018-09-26 11-19-58.png)

- If the poles are in the red area, overshoot spec is met

## 4.3.2 Settling Time

- The smallest time $$T_s > 0$$ such that

$$(\forall t\geq T_s)\frac{y_{s.s.}-y(t)}{|y(t)|}\leq 0.02$$, $$2\%$$ settling