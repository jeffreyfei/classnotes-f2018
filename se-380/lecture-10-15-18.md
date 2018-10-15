## Approximations to *sketch* Bode plot

i) For $$\omega \leq \frac{1}{\tau}$$, $$Im(G(j\omega))\approx 0$$

$$\Rightarrow (\forall \omega \leq \frac{1}{\tau}) 20\log |G(j\omega )|\approx 20\log |1| = 0dB$$

ii) For $$\omega > \frac{1}{\tau}, Re(G(j\omega))\approx 0$$

$$\Rightarrow (\forall \omega > \frac{1}{\tau}) 20\log |G(j\omega)|\approx 20\log |\tau\omega|$$

$$\frac{1}{\tau}=``break frequency"$$

![](/assets/Screenshot from 2018-10-15 10-52-00.png)

Error introduced by approximation is largest at $$\omega=\frac{1}{\tau}$$. Actual magnitude is $$20\log G(j\frac{1}{\tau})=20\log |j+1|\approx 3dB$$

iii) $$ G(s)+\tau s\pm 1, \tau > 0$$

a) $$G(s)=\tau s +1$$, $$G(j\omega)=j\omega\tau + 1)$$

##### Polar plot

![](/assets/Screenshot from 2018-10-15 10-56-30.png)

##### Bode plot

$$20\log |G(j\omega)|=20\log |j\omega \tau +1|$$
$$\angle G(j\omega)=\angle j\omega \tau +1$$

#### Approximation to *sketch* Phase Bode plot

i) For $$\omega << \frac{1}{\tau}$$, $$\angle G(j\omega)\approx j0 + 1 = 0^0$$

From the polar plot we see

- Magnitude plot will be unchanged from case (a)
- Phase plot changes: goes from 180 degrees at low frequency to 90 degrees at high frequencies


### Ex.

$$G(s)=\frac{100}{s+10}=\frac{100}{10}\frac{1}{\frac{s}{10}+1}=10\frac{1}{\frac{s}{10}+1}$$

Frequency Response: $$G(j\omega)=\frac{10}{\frac{j\omega}{10}+1}$$

$$20\log |G(j\omega)|=20\log |10|-20\log |\frac{j\omega}{10}+1|$$

$$\angle G(j\omega)=\angle 10-\angle (\frac{j\omega}{10}+1)$$

![](/assets/Screenshot from 2018-10-15 11-17-39.png)

The bandwidth of this sytem is the smallest frequency at which

$$|G(j\omega_{BW})|=\frac{1}{\sqrt 2} G(0)$$

(in dB: $$20\log |G(j\omega_{BW})|=20\log |G(s)|-3$$)

Easy to read from Bode plot: in this case 10 rad/s