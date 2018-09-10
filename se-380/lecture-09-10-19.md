# Chapter 1
## 1.3.1 (Web Server)


### Objective
- Keep buffer size at a constant, non-zero, value $$r(t)$$, (this ensures (1) time to process requests isn't too large (ii) server isn't under/utilized

- The difficulty is that the server's service rate is unknown - it depends on many things - we'll model it as an unknown distance $$d(t)$$
- The control objective is to manage the client request rate $$u(t)$$ given $$r(t)$$ and $$y(t)$$

$$\frac{dy(t)}{dt} = u(t)-d(t)$$

![](/assets/Screenshot from 2018-09-10 10-46-50.png)

Control engineering attemps to change the behaviour of a system (plant) in a useful way despite the presence of external inflluence (disburbances) and despite model uncertainty.

![](/assets/Screenshot from 2018-09-10 10-50-01.png)

This is typically done by inter connecting the plant with another system (controller). Feedback is the most power interconnection architecture

### Signals

$$r(t)$$ - reference command
$$y(t)$$ - plant output
$$u(t)$$ - controller output
$$d(t)$$ - disturbance
$$n(t)$$ - sensor noise

### Systems

Plant, Controller, Sensor

### Control Cycle

1. **Sense** operation of system
2. Compare against desired behaviour
3. **Compute** corrective actions informed by a model of system's reponse to external stimulus
4. **Actuate** the system to effect the desired cycle


```
sense -----> compute ------> actuate
 /|\                           |
  |____________________________|
```

## 1.3 Design Cycle

1. Study system to be controlled; decided on sensors and activators (e.g. Camera vs L, I, D, A, R
2. Model Resulting System
 - By model we mean a mathematical model
 - Often one or more differential equations, e.g. follower
 - Model obtained through analysis and/or experienments
3. Simply model if necessary
 - Classical control (this course, most prevelant) requires that we have linear time-invariant plant, so it has a **transfer function**
 
 **e.g. Follower:**
 
 $$sx_f(s)-x_f(0)=U(s)$$
 
 => $$x_f(s)=\frac{1}{s} U(s)$$    $$(x_f(0)=0)$$
 
 $$\frac{1}{s}$$ is the **transfer function**

4. Analyse reuslting model
5. Determine design specs
 - Stability, good *steady-state behaviour*; *robustness* to model uncertainty, good *transient behaviour*
6. Decide on the type of controller
 - In this course the controller itself is a *transfer function*
7. Design controller
8. Simulate closed-loop system
 - Usually MATLAB, also Octave, Scilab
9. Return to Step 1 if needed
10. Implement an actual system


# Chapter 2 (Mathematical Models of Systems)
- For control design, we need a "good" mathematical model of plant
- good = simple but accurate
- no model is perfet
- complexity trade-off - design (simple) vs. simulation (complex)

##### Example (Damper)

![](/assets/Screenshot from 2018-09-10 12-39-11.png)