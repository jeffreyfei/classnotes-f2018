**Anti-wind up** - deals with actuator constraints
    - Idea: when actuator hits its limit, stop integrating
    - See section 7.4
    
##### Consider    
    
$$u(t)=K_p e(t)+\frac{K_p}{T_i}\int_0^t e(\tau)d\tau + K_p T_d \frac{de}{dt}$$

**Proportional part**
- Can feedback stabilize open-loops stable plants
- Depends on the current value of $$e(t)$$
- High $$K_p$$ values usually improve s.s. performance
- If $$K_p$$ is too high, may lose stability


**Integral part**
- Gives perfect step tracking
- Acts on accumulated error
- Depends on the area under the curve (the history)

**Derivative part**
- Penalizes fast changes in $$e(t)$$, tends to smooth out transients
- Sometimes called the "predictive" part of PID

Consider P.D. $$u(t)=K_p(e(t)+T_d \frac{de(t)}{d(t)})$$
- The tracking error $$T_d$$ seconds into the future, using linear interpolation

#### PID Controller Standard Form

$$C(s)=\frac{g_2 s^2+g_1 s + g_0}{s^2+f_1s}$$

$$K_p= \frac{g_1 f_1 - g_0}{f_1^2}$$
$$T_i = \frac{g_1 f_1 - g_0}{g_0 f_1}$$
$$T_d = \frac{g_0 - g_1 f_1 - g_2 f_1^2}{f_1(g_1f_1-g_0)}$$
$$\tau_d=\frac{1}{f_i}$$

#### Assumption 7.3.2

The plant $$P(s)$$ is

$$\frac{b_s+b_0}{s^2+a_1s + a_0}, b_0\neq 0$$

- Needed to avoid unstable pole zero cancellations

$$\pi(s)=D_p D_c + N_p N_c$$

$$=s^4 + (a_1+f_1+b_1q_2)s^3+(a_0+a_1f_1+b_1q_1+b_0q_2)s^2+(a_0f_1+b_1q_0+b_0q_1)s+b_0 q_0$$

- Now say we want the closed-loop poles to be located at $$\{\lambda_1, \lambda_2,\lambda_3,\lambda_4\}\subset \mathbb C^{-}$$

- The desired poles are picked based on desired settling time $$\%OS, T_p$$ etc.

- Desired pole locations, determine a desired characteristic polynomial

$$\pi^{des}(s)=(s-\lambda_1)(s-\lambda_2)(s-\lambda_3)(s-\lambda_4)$$

$$=: s^4+\alpha_3 s^3+\alpha_3 s^3 + \alpha_2 s^2+\alpha_1 s + \alpha_0, \alpha_i \in \mathbb R$$

- Equate coefficient of $$\pi$$ and $$\pi^{des}$$

- Can place them into a matrix