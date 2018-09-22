iii) Moving blocks

![](/assets/Screenshot from 2018-09-21 10-43-29.png)

$$Y(s)=D(s)+G(s)U(s)$$

iv) Feedback
![](/assets/Screenshot from 2018-09-21 10-49-30.png)
$$\equiv Y(s)=G(s)(U(s)-G_2(s)Y(s))$$

##### Strategy 1: Write equation for Y(s) and re-arrange

$$Y(s)=G_2(s)[G_{ff}(s)U(s)+G_1(s)(U(s)-Y(s)]$$
$$\Rightarrow\frac{Y(s)}{U(s)}=\frac{G_2G_{ff}+G_2G_1}{1+G_1(s)G_2(s)}$$

##### Strategy 2: Re-arrange blocks to reveal common configs

![](/assets/Screenshot from 2018-09-21 10-55-58.png)

i) Move $$G_1$$ to the left

![](/assets/Screenshot from 2018-09-21 22-24-17.png)

ii) Swap order of summing nodes

![](/assets/Screenshot from 2018-09-21 22-32-35.png)

$$Y(s)=(G_1+G_{ff})(\frac{G_2}{1+G_1G_2})U(s)$$

### Systematic Method

1) Introduce new variables $$\{v_1, v_2,...\}$$ at the out[put of each summing node
2) Write expression for *inputs* to summing nodes in terms of $$\{u, y, v_1, v_2,...\}$$
3) Write equation for each summer and $$y$$
4) Eliminate $$\{v_1, v_2,...\}$$

![](/assets/Screenshot from 2018-09-21 22-42-48.png)

Steps 3

$$y=G_3G_2v_2$$
$$v_2=G_1v_1+H_3y-H_2G_2v_2$$
$$v_1=u-H_1G_2v_2$$

Steps 4 - Solve for Y. Use Crammer's rule

$$\begin{bmatrix}
1 & H_1 G_2 & 0\\
-G_1 & 1+H_2 G_2 & -H_3\\
0 & -G_3G_2 & 1
\end{bmatrix}
\begin{bmatrix}
v_1\\
v_2\\
y
\end{bmatrix}
=
\begin{bmatrix}
u\\
0\\
0
\end{bmatrix}
$$

$$Y=
\frac{
\det\begin{bmatrix}
1 & H_1G_2 & u\\
-G_1 & 1+H_2G_2 & 0\\
0 & -G_2 G_3 &0
\end{bmatrix}
}{
\det\begin{bmatrix}
1 & H_1G_2 & 0\\
-G_1 & 1+H_2G_2 & -H_3\\
0 & -G_2G_3 & 1
\end{bmatrix}
}=
\frac{G_1G_2G_3 \cdot u}{(1+H_2+G_2)-G_2G_3H_3-(-G_1)[H_1G_2]}$$

## Chapter 4: 1st and 2nd Order Systems

### First Order

$$\tau\dot y+y=ku, \tau, k\in\mathbb{R}$$
or
$$\frac{Y(s)}{U(s)}=\frac{k}{\tau s+1}$$
or
$$\dot x=\frac{-1}{\tau}x+\frac{k}{\tau}u$$
$$y=x$$

### Second Order

$$\ddot y+2z\omega_n\dot y+\omega_n^2 y=k\omega_n^2u$$
or
$$\frac{Y}{U}=\frac{k\omega_n^2}{s^2+2z\omega_n s+\omega_n^2}$$
or, with $$x=\begin{bmatrix}y\\ \dot y\end{bmatrix}$$

$$\dot x=\begin{bmatrix}
0 & 1\\
-\omega_n^2 & -2z\omega_n
\end{bmatrix}x+
\begin{bmatrix}
0\\
k\omega_n^2
\end{bmatrix}
n
$$
$$y=\begin{bmatrix}1 & 0\end{bmatrix}x$$

**Objective**: Understand relationship between pole locations and time-domain behaviour

### 4.1 1st Order

Pole: $$s=\frac{-1}{\tau}$$
Zeroes: none
Steady-state gain: $$k$$
Bandwidth: $$\frac{1}{\tau}$$

![](/assets/Screenshot from 2018-09-21 11-21-07.png)

$$\frac{Y(s)}{U(s)}=\frac{k}{\tau s+1}$$

$$Y(s)=G(s)U(s)$$

$$U(s)=1$$ when $$U(t)$$ is an impulse