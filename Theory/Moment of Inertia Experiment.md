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
- $l$ = $0.18 \;m$
- Timing
| Time | # of Oscillations | Period |
| - | - | - |
| $8.64 \;s$ | 10 | $0.864 \;s$ |
| $8.68 \;s$ | 10 |$0.868 \; s$|
| $9.14 \; s$ | 10 | $0.914\;s$|
| $8.98 \;s$ | 10 | $0.898\;s$ |
	- Average period: $0.886\;s$

Calculation: 
- Without g seems to be in the same magnitude

**Experimental Data: Yaw**
- $l$ = $0.18 \;m$
- $d = 0.172\;m$
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

#### A. Rolling
- $l = 0.33 \;m$
- Timing
| Time | # of Oscillations | Period |
| - | - | - |
| $11.92\;s$ | 10 | $1.192\;s$ |
| $11.95\;s$ | 10 |$1.195\; s$|
| $11.97\; s$ | 10 | $1.197\;s$|
| $12\;s$ | 10 | $1.200\;s$ |
	- Average period: $1.196\;s$

#### B. Pitching
- $l = 0.31\;m$
- Timing
| Time | # of Oscillations | Period |
| - | - | - |
| $11.39 \;s$ | 10 | $1.139 \;s$ |
| $11.27 \;s$ | 10 |$1.127 \; s$|
| $11.74 \; s$ | 10 | $1.174 \;s$|
| $11.27 \;s$ | 10 | $1.127\;s$ |
	- Average period: $1.14175\;s$

#### C. Yawing
- $l = 0.17\;m$
- $d = 0.15\;m$
- Timing
| Time | # of Oscillations | Period |
| - | - | - |
| $9.49 \;s$ | 10 | $0.949 \;s$ |
| $9.56 \;s$ | 10 |$0.956 \; s$|
| $9.41 \; s$ | 10 | $0.941 \;s$|
| $9.17 \;s$ | 10 | $0.917 \;s$ |
	- Average period: $1.14175\;s$


## Appendix: References
- [NASA X56 Moment of Inertia Experiment](https://www.youtube.com/watch?v=7xQJ2sVQrUA)
- [Physical Pendulum Torque](https://phys.libretexts.org/Bookshelves/University_Physics/Book%3A_University_Physics_(OpenStax)/Book%3A_University_Physics_I_-_Mechanics_Sound_Oscillations_and_Waves_(OpenStax)/15%3A_Oscillations/15.05%3A_Pendulums)
- 


#theory 