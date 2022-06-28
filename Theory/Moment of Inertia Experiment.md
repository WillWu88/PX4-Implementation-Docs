# Experiment: Determining the Moment of Inertia

## 1. Motivation, Background
The goal of this experiment is to empirically determine the moment of inertia of our experimental aircraft. Specifically, there are three moments of inertia associated: $I_{xx}$, $I_{yy}$ and $I_{zz}$ 

Aircraft Moment of Inertia (physical pendulum) 
$$I = \frac{T^2ml}{4\pi^2} - \frac{ml^2}{g}$$
Aircraft Moment of Inertia (torsion pendulum)
$$I = \frac{md^2T^2g}{16\pi^2l}$$
- $T$ is the oscillation period
- $l$ is the length of the string
- $d$ is the distance between strings of the bifilar pendulum

We are ignoring the string moment of inertia, assuming the strings have negligible weight

Questions:
- where is the $g$ term?
	- run the same experiment on parrot mini drone and compare results
	- Unit doesn't match without g!

## 2. Experiments

### I. Verification Experiment: Parrot Mambo Mini
- The goal is to verify our calculations. 
- 2 runs, 10 oscillations per cycle, rolling rotations along the x axis
- Previously obtained data
 | Property | Value |
 | - | -|
 | Mass | 0.0683 kg |
 |$I_{xx}$| $0.69 \cdot 10^{-4} \: kgm^2$|
 |$I_{yy}$| $0.775 \cdot 10^{-4} \: kgm^2$|
 |$I_{zz}$| $1.5 \cdot 10^{-4} \: kgm^2$| 

**Experimental Data**: Roll
- $d$ = $0.068 \;m$
- $l = 0.29 \; m$
- Timing
| Time | # of Oscillations | Period |
| - | - | - |
|$9.45\;s$ | 10 | $0.945\;s$ (test)|
| $9.35 \;s$ | 10 | $0.935 \;s$ |
| $9.45 \;s$ | 10 |$0.945 \; s$|
| $9.38 \; s$ | 10 | $0.938 \;s$|
| $9.16 \;s$ | 10 | $0.916 \;s$ |
	- Average period: $0.9335 \;s$

Calculation: 
- $I_{xx} = 5.895 \cdot 10^{-5} \; kgm^2$
- Error percentage: $15\%$


**Experimental Data: Yaw**
- $l$ = $0.18 \;m$
- $d = 0.072\;m$
- Timing
| Time | # of Oscillations | Period |
| - | - | - |
| $10.61 \;s$ | 10 | $1.061\;s$ |
| $10.51 \;s$ | 10 |$1.051 \; s$|
| $10.49 \; s$ | 10 | $1.049\;s$|
| $11.09\;s$ | 10 | $1.149\;s$ |
	- Average period: $1.0775\;s$

Calculation, with g:
$$I = \frac{md^2T^2g}{16\pi^2l} = \frac{0.0683kg\cdot (0.07m)^2\cdot(1.0775s)^2\cdot 9.8m/s^2}{16\cdot\pi^2\cdot0.18m} = 1.33\cdot10^{-4}kgm^2$$ 
### II. Experimental Data for Quadcopter
- Mass: $0.705\;kg$

#### A. Pitching
- $l = 0.40\;m$
- $d =0.177 \;m$
- Timing
| Time | # of Oscillations | Period |
| - | - | - |
| $8.64 \;s$ | 10 | $0.864 \;s$ |
| $8.75 \;s$ | 10 |$0.875 \; s$|
| $8.49 \; s$ | 10 | $0.849 \;s$|
| $8.61 \;s$ | 10 | $0.861 \;s$ |
	- Average period: $0.862 \;s$
- Calculation: $$I_{yy} = 2.549 \cdot 10^{-3}\;kgm^2$$

#### B.Rolling
- $l = 0.35\;m$
- $d= 0.265\;m$
- Timing
| Time | # of Oscillations | Period |
| - | - | - |
| $6.88 \;s$ | 10 | $0.688 \;s$ |
| $6.97 \;s$ | 10 |$0.697 \; s$|
| $6.80 \; s$ | 10 | $0.680 \;s$|
| $6.42 \;s$ | 10 | $0.642 \;s$ |
	- Average period: $0.677 \;s$
- Calculation: $$I_{xx} = 4.028 \cdot 10^{-3}\;kgm^2$$

#### C. Yawing
- $l = 0.17\;m$
- $d = 0.15\;m$
- Timing (needs fixing)
| Time | # of Oscillations | Period |
| - | - | - |
| $9.49 \;s$ | 10 | $0.949 \;s$ |
| $9.56 \;s$ | 10 |$0.956 \; s$|
| $9.41 \; s$ | 10 | $0.941 \;s$|
| $9.17 \;s$ | 10 | $0.917 \;s$ |
	- Average period: $1.241\;s$
- Yawing moment calculation:
$$I = \frac{mgd^2T^2}{16\pi^2l} = \frac{0.705kg\;\cdot\;9.8m/s^2\;\cdot\;(0.148m)^2\;\cdot\;(1.241s)^2}{16\pi^2\;\cdot\;0.28m} = 5.279\cdot10^{-3}\;kgm^2$$

## Appendix: References
- [NASA X56 Moment of Inertia Experiment](https://www.youtube.com/watch?v=7xQJ2sVQrUA)
- [Physical Pendulum Torque](https://phys.libretexts.org/Bookshelves/University_Physics/Book%3A_University_Physics_(OpenStax)/Book%3A_University_Physics_I_-_Mechanics_Sound_Oscillations_and_Waves_(OpenStax)/15%3A_Oscillations/15.05%3A_Pendulums)
- [Bifilar torsion pendulum]


#theory 