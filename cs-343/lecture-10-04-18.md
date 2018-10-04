## Amdahl's Law

$$S_c=\frac{1}{(1-P)+P/C}$$ where $$T_1=1, T_c=sequential+concurrent$$

- We can see that as C (number of CPUs) goes to $$\infty$$, the speed up equals
to $$\frac{1}{(1-P)}$$, which is dependant on the sequantial section of the program.
The greater the $$P$$, the less speedup we get.


#### COBEGIN/COEND

- Potentially creates multiple threads for procedures with the `BEGIN ... END` keyword
defined in the cobegin block
- Which thread gets scheduled first is undeterministic