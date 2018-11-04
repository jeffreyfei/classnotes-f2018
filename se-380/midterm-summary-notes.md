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