# System Theroy (And Related Mathematics)

### Second Order Differential Equations
- Consider a differential equation
$$My'' + by' + ky = 0$$
	- Natural frequency, $\omega_n$ :
	$$\omega_n = \sqrt{\frac{k}{M}}$$
	- Damping ratio, $\xi$: 
	$$\xi = \frac{\omega_n b}{2}$$
#### Side note: $\xi$ and multiplying $\xi$ by 2
Personal theory: in a second order linear system with input, the above differential equation usually takes the denominator. The above formulation allows the transfer function to take the term of:
$$H(s) = \frac{\omega_n^2}{s^2 + 2\xi\omega_n s + \omega_n ^2}$$
The poles can easily be determined from this form


### References:
- [Second Order Diff EQ](https://www.sciencedirect.com/topics/engineering/second-order-system)

#theory 