### Cor 5.2.8

If there is an unstable pole-zero cancellation, then the feedback system isn't I.O. stable

##### Proof:

Suppose there is an unstable cancellation at $$\lambda$$, $$Re(\lambda)\geq0$$

Then

$$\pi(\lambda)=N_{p}(\lambda)N_c{\lambda}+D_p(\lambda)D_c(\lambda)=0+0=0$$

So $$\pi$$ has a bad root, so by Thm 5.2.6, feeback system is not I.O stable

### 5.2.3 Internal Stability and I.O Stability

It can be shown that roots of $$\pi(s)\subseteq$$ eigenvalues of $$A_{CL}$$

so, Internal stability $$\Rightarrow$$ I.O stability

The converse is false in general, but holds for many practical applications

### 5.3 The Routh-Hurwitz Criterion

Consider an n^{th} order poly: $$\pi(s)=s^n+a_{n-1}s^{n-1}+...+a_1s+a_0$$

##### Defintion:

$$\pi(s)$$ is Hurwtiz, if all its roots have $$Re(s)<0$$

- The R.H. criterion is a test that tells us if a polynomial is Hurwitz without finding its roots

### The Routh-Hurwitz Criterion

If $$\pi$$ is Hurwiz, then $$a_0>0$$ for all $$i\in\{1,...,n-1\}$$

#### Ex. 5.3.1

$$s^4+3s^3-2s^2+5s+6\Rightarrow$$ Not Hurwitz

$$s^2+5s+6\Rightarrow$$ Not Hurwitz

$$s^3+5s^2+9s+1\Rightarrow$$ Don't know

|||||||
|---|---|---|---|
|$$s^n$$|1|$$a_{n-2}$$|$$a_{n-4}$$|$$a_{n-6}$$|...|
|$$s^{n-1}$$|$$a_{n-1}$$|$$a_{n-3}$$|$$a_{n-5}$$|$$a_{n-7}$$|...|
|$$s^{n-3}$$|$$r_{2,0}$$|$$r_{2, 1}$$|$$r_{2, 2}$$|$$r_{2, 3}$$|...|
|...|...|...|...|...|...|
|$$s^2$$|$$r_{n-1, 0}$$|$$r_{n-2}$$||||
|$$s^1$$|$$r_{n-1, 0}$$|||||
|$$s^0$$|$$r_{n, 0}$$|||||

$$r_{2, 0}:=\frac{a_{n-1}\cdot a_{n-2}-(1)a_{n-3}}{a_{n-1}}$$

$$r_{2, 1}:=\frac{a_{n-1}a_{n-4}-(1)a_{n-5}}{a_{n-1}}$$

$$r_{2, 2}:=\frac{a_{n-1}\cdot a_{n-6}-(1) a_{n-7}}{a_{n-1}}$$

- The 4th row is computed from the 2nd and 4rd row using the same pattern


$$r_{3, 0}:=\frac{r_{2, 0}a_{n-3}-a_{n-1}r_{2, 1}}{r_{2, 0}}$$

- Continue along each row until you get zeros
- Terminate early if we ever get a zero in 1st column

### Thm 5.3.3 (Routh-Hurwitz Criterion)

1. $$\pi(s)$$ is Hurwitz if and only if all elements in 1st column have the same sign

2. If there are no zero in the first column, then the number of sign changes in 1st column = # of bad roots
    - Also means no roots on $$\mathbb R$$ axis