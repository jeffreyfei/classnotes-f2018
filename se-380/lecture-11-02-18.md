#### Ex 7.3.1

- Rearrange the plant in the form shown in 7.3.2

$$P(s)=\frac{b_1 s+b_0}{s^2 +a_1 s + a_0}$$

- Identify the terms $$a_0, a_1, b_0, b_2$$

- Use transient specs to define a good region in the complex plane where the roots of $$\pi(s)$$ should be

- Expand the desired characteristic polynomial to the form outlined in 7.3.3

$$s^4 + \alpha_3 s^3 + \alpha_2 s^2 + \alpha_1 s + \alpha_0$$

- Identify the terms $$\alpha_1, \alpha_2, \alpha_3, \alpha_0$$

- Fill the matrix in 7.3.3 with the appropriate terms

- Solve to obtain gains to the corresponding PID controller

#### 1st Order + Time Delay

$$P(s)=\frac{K}{\tau s + 1}e^{-sT}$$

##### Pode approximation of irrational term

$$e^{-sT} \approx \frac{-s T/2 + 1}{s T/2 + 1}$$

Now $$P(s)\approx \frac{K}{\tau+1}\frac{-sT+2}{sT+2}$$

**Remark:** Time delay of T seconds acts like a non-minimum phase zero at $$s=\frac{2}{T}$$, the bigger the delay, the "worse" the zero


## Chapter 4

- Design specs will be in the frequency domain, e.g. bandwidth gain margin and phase margin

- Since our real interest is how the system behaves in physical time, in this chapter we'll use the relationships between time and frequency domains

- Will take time-domain specs like $$T_s$$, $$\%OS$$ and convert them to frequency domain specs