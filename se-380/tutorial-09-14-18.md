## Problem Set 1

e) $$\frac{1+j}{\cos(-4\pi/5)+j\sin(-4\pi/5)}$$

Polar form:
![](/assets/Screenshot from 2018-09-14 12-39-59.png)
$$=\frac{1+j}{e^{-4/5\pi j}}$$
$$=\sqrt{2} \frac{ e^{\pi/4j}}{e^{-4/5\pi j}}$$
$$=\sqrt{2} e^{(\pi/4+4\pi/3)j}$$

$$|z|=\sqrt{2}$$

$$\arg z=\frac{\pi}{4}+\frac{4}{5}\pi=\frac{21}{20}\pi=\frac{-19}{20}\pi$$

2)
a) Prove $$\overline{zw}=\bar{z}\bar{w}$$

Let $$z=a+jb, w=c+jd$$

$$\overline{zw}=\overline{(a+jb)(c+jd)}$$
$$=\overline{(ac-bd)+j(bc+ad)}$$
$$=(ac-bd)-j(bc+ad)$$
$$=(ac-(-b)(-d))+j(-bc-ad)$$
$$=(ac-(-b)(-d))+j((-b)(c)+a(-d))$$
$$=(a-jb)(c-jd)=\bar{z}\bar{w}$$

4)

$$A=\begin{bmatrix}
s+3 & 1\\
-4 & s+2
\end{bmatrix},
s\in\mathbb{C}
$$

$$A^{-1}=\frac{1}{\det A}
\begin{bmatrix}
s+2 & -1\\
4 & s+3
\end{bmatrix}
=\frac{1}{(s+3)(s+2)-(-4)(1)}
\begin{bmatrix}
s+2 & -1\\
4 & s+3
\end{bmatrix}
$$

$$=\frac{1}{s^2+5s+10}
\begin{bmatrix}
s+2 & -1\\
4 & s+3
\end{bmatrix}
$$

### Ex.1

Consider $$f:\mathbb{R}\rightarrow\mathbb{C}$$
$$f(\omega)=1+j\omega$$

**Note**

1. $$\lim_{\omega\rightarrow\pm \infty} f(\omega)=\pm \infty$$ (vertically)
2. $$f(0)=1\in\mathbb{R}$$
3. $$f(1)=1+j=\sqrt{2} e^{\frac{\pi}{4}j}$$

![](/assets/Screenshot from 2018-09-14 13-05-54.png)

$$f(\omega)$$ for $$\omega \in \mathbb{R}$$
$$f(1)=1-j, f(1)=1+j$$e

$$|f(0)|=1$$
$$\angle f(0)=0$$
##### Magnitude graph

$$|f(\omega)|=\sqrt{1+\omega^2}$$
$$\angle f(\omega)=\arctan(\omega)$$ for $$\omega \geq 0$$

![](/assets/Screenshot from 2018-09-14 13-00-29.png)

##### Phase graph

If $$w>>1$$

$$|f(\omega)|\approx \sqrt{\omega^2}=\omega$$

$$\lim_{\omega\rightarrow\infty} {\arctan{(\omega)}=\frac{\pi}{2}}$$

![](/assets/Screenshot from 2018-09-14 13-03-49.png)