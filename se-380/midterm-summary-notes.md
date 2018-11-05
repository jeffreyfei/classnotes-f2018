#### LTI Formula

$$\dot x= Ax+Bu$$, where $$A\in \mathbb R^{n\times n}, B\in \mathbb R^{n\times m}$$
$$y=Cx+Du$$, where $$C\in \mathbb R^{p\times n}, D\in\mathbb R^{p\times m}$$

#### Linearization

$$f(x)=f(\bar x)+\frac{\partial f}{\partial x}|_{x=\bar x}(x-\bar x) + $$ higher order terms

$$\frac{\partial f}{\partial x}|_{x=\bar x}=Jacobian$$

With $$u$$

$$\dot{\delta x}=f(x, u)=f(\bar x, \bar u)+A\delta x+B\delta u$$

$$A:=\frac{\partial f}{\partial x}|_{(\bar x, \bar u)}$$

$$B:=\frac{\partial f}{\partial u}|_{(\bar x, \bar u)}$$

$$\delta y=C\delta x+D\delta u$$

$$C:=\frac{\delta h}{\delta x}|_{(\bar x, \bar u)}$$

$$D:=\frac{\delta  h}{\delta u}|_{(\bar x, \bar u)}$$

#### Laplace Table

![](/assets/Screenshot from 2018-11-03 22-33-02.png)

![](/assets/Screenshot from 2018-11-03 22-34-03.png)
![](/assets/Screenshot from 2018-11-03 22-34-14.png)

#### Derived TF Function

$$G(s)=C(sI-A)^{-1}B+D$$
$$=C\frac{adj(sI-A)}{det(sI-A)}B+Dn$$

$$\frac{Y(s)}{U(s)}=\frac{\det\begin{bmatrix}
sI-A & B\\
-C & D
\end{bmatrix}}{
\det(sI-A)
}$$

- Internal stability is asymptotic stability of all the states in the system

#### Negative Feedback
$$ G(t)=\frac{G_{eq}}{1+H_{eq} G_{eq}}$$

where $$G_{eq}$$ is the plant, $$H_{eq}$$ is the feedback


#### Find Second Order System

- Find %OS by take the value of the actual peak and and stead state gain

$$\%OS=\frac{y_{peak}-G_{ss}}{G_{ss}}$$

- Solve $$\varepsilon$$ with the formula and $$\%OS$$
- Solve $$\omega_n$$ using the peak to peak formula

#### Damping Ratio

![](/assets/Screenshot from 2018-11-04 21-45-27.png)

#### Steady-state Gain

![](/assets/Screenshot from 2018-11-04 22-04-20.png)

#### Oscillatory Frequency

$$\omega_n\sqrt{1-\varepsilon^2}$$

#### First Order System Allowable S-plane Region

$$\frac{-4}{T_s}$$

#### Asymptotic Stability

![](/assets/Screenshot from 2018-11-04 23-10-26.png)

#### Eigenvalues

$$\det (A-\lambda I_n)=0$$

#### Matrix Exponential

$$\mathcal L\{e^{At}\}=(sI-A)^{-1}$$

#### Final Value Theorem

$$\lim_{t\rightarrow\infty} f(t)=\lim_{s\rightarrow 0} sF(s)$$