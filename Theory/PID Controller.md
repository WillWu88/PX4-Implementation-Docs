# PID Controller

## 1. Formulation, Set up

### A. System Convention
- We have a plant $G$, Controller $K$, reference $R$, state feedback $x$ and error $e$. Our goal is to reduce $e$ to $0$ asymptotically.
- **System is stable and controllable**
- Close loop transfer function $H(s)$
$$H(s) = \frac{G(S)K(S)}{1+G(S)K(S)}$$

### B. Steady State Error
- Steady state error, $e(\infty) = \lim\limits_{t \to \infty} e(t)$
- Using final value theorem:
$$E(\infty) = \lim\limits_{s \to 0} sE(s) = \lim\limits_{s \to 0} = s(1-H(s))R(s) = \frac{sR(s)}{1+G(s)K(s)} $$

### C. P Controller
- Controller is a simple proportional gain, denoted by the parameter $k_p$
$$C(t) = k_p \cdot e(t),\; C(s) = k_p E(s)$$
$$\therefore K(s) = \frac{C(s)}{E(s)} = k_p$$
- P controller does not eliminate steady state error:
	- Let $R(s) = \frac{1}{s}$
	$$E(\infty) = \lim\limits_{s \to 0} \frac{1}{1+k_pG(S)}$$
	- For $E(\infty)$ to be $0$, gain $k_p$ must appraoch $\infty$, which is impossible in real applications.

### D. PI Controller
- Refer to [[System Theory]] for second order systems, damping ratio and natural frequency
- Controller is the sum between proportional gain $k_p$ and past-present integration multiplied by gain $k_i$
$$C(t) = k_p\cdot e(t) + k_i \int_0^t e(\tau)d\tau,\;C(S) = k_pE(s)+\frac{k_iE(s)}{s}$$
$$\therefore K(s) = \frac{C(s)}{E(s)} = k_p + \frac{k_i}{s}$$
- The addition of integration eliminates steady state error, but introduces overshooting
- PI locks the damping ratio with natural frequency; one cannot tune them separately.

### E. PD Controller
- Controller is the sum between proportional gain $k_p$ and present-past differentiation multiplied by gain $k_d$
$$C(t) = k_p\cdot e(t) + k_d \frac{d}{dt}e(t),\;C(S) = k_pE(s)+k_d sE(s)$$
$$\therefore K(s) = \frac{C(s)}{E(s)} = k_p + sk_d$$
- PD controller also does not eliminate steady state error, but it increases rise time and eliminates over-shooting
- It also allows us to tune the damping ratio and natural frequency of the system separately. 




## References
-  [Excellent PID Notes by MapleSoft](https://www.maplesoft.com/content/EngineeringFundamentals/12/MapleDocument_12/PID%20Control.pdf)
- [PID Theory (rise time, overshoot, etc)](https://www.ni.com/en-us/innovations/white-papers/06/pid-theory-explained.html)



#theory