## 4.1 First order

$$Y(s)=\frac{k}{\tau s+1}U(s)$$

$$G=\tau s+1$$

Steady state gain: $$G(o)=k$$

Impulse response: $$G(t)=\mathcal{L}(G(n))=\frac{k}{\tau}e^{\frac{t}{\tau}}, t\geq 0$$

![](/assets/Screenshot from 2018-09-24 10-47-37.png)

$$g(0)=\frac{k}{\tau}$$
$$g(\tau)=\frac{k}{\tau}e^{-1}\approx 0.37\frac{k}{\tau}$$
$$g(2\tau)=\frac{k}{\tau}e^{-1}\approx 0.14\frac{k}{\tau}$$

Higher Bandwidth:

$$\frac{1}{\tau}\Leftrightarrow$$ Faster Decay

### Step Response

Pick $$u(t)=1(t)$$ (unit step function)

Then $$u(s)=\frac{1}{S}$$ so $$Y(s)=\frac{k}{\tau s+1}-\frac{1}{s}$$

and

$$y(t)=\mathcal{L}^{-1}\{Y(s)\}=\mathcal{L}^{-1}\{\frac{k}{s}-\frac{k}{s+1/\tau}\}=
k(1-e^{-t/\tau}), t\geq 0$$
- Partial fraction expansion

![](/assets/Screenshot from 2018-09-24 10-51-38.png)

$$y(0)=, y(\tau)\approx 0.631k, y(2\tau)=0.85k, y(4\tau)\approx 0.98k$$

### Observations

1. After $$4\tau$$ seconds, $$y$$ is within 2% of its steady-state value (setting time)

2. $$y(t)\leq k$$ for all $$+\geq 0$$ (no overshoot)

3. $$y(t)$$ is monotonically increasing (no peaking)

    - Higher bandwidth $$1/\tau \Leftrightarrow$$ faster response


- The constant $$\tau$$ (time constant of system) completely determines how fast the system responds

#### Side

![](/assets/Screenshot from 2018-09-24 10-59-06.png)

$$\frac{|G(j\omega_{BW}|}{|G(0)|}=\frac{1}{\sqrt{2}}$$

- This relation is also in the course notes


## 4.2 Second order system

$$Y(s)=G(s)U(s), G(s)=\frac{k\omega_n^2}{s^2+2z\omega_n s+\omega_n^2}$$

### Ex. 4.2.1

$$M\ddot q =u-K_{spring} q-b\dot q$$

$$y=q$$

$$\frac{Y(s)}{U(s)}=\frac{1/M}{s^2+\frac{b}{M}s+\frac{K_{spring}}{M}}$$

For this sytem

$$\omega_n=\sqrt{\frac{K_{spring}}{M}}, z=\frac{b}{2\sqrt{MK_{spring}}}, K=\frac{1}{K_{spring}}$$

#### Pole locations

$$s=-z\omega_n\pm\omega_n \sqrt{z^2-1}=\omega_n(-z\pm\sqrt{z^2-1}), \omega_n >0$$

![](/assets/Screenshot from 2018-09-24 11-09-46.png)

Pole locations $$z$$ goes from 0 to $$+\infty$$

$$G(s)=\frac{K\omega_n^2}{s^2+2z\omega_n s+\omega^2}$$

The value of $$z$$ is used to categorize (see illustration above and below)

- G is *undamped* if $$z=0$$
- G is *underdamped* if $$0<z<1$$ (red)
- G is *critically damped* if $$z=1$$ (yellow)
- G is *overdamped* if $$z>1$$

![](/assets/Screenshot from 2018-09-24 11-15-30.png)

### Terminology

$$z$$ - damping ratio

$$\omega_n$$ - undamped natural frequency

$$K$$ - steady-state gain


## 4.2.1 Underdamped Systems

$$s=-z\omega_n \pm \omega_n \sqrt{z^2-1}=\omega_n(-z\pm\sqrt{z^2-1})$$

$$=-z\omega_n \pm j\omega_n\sqrt{1-z^2}=\omega_ne^{\pm j (\pi -\theta)}$$

![](/assets/Screenshot from 2018-09-24 11-20-44.png)