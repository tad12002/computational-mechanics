---
jupytext:
  formats: notebooks//ipynb,md:myst
  text_representation:
    extension: .md
    format_name: myst
    format_version: 0.13
    jupytext_version: 1.11.4
kernelspec:
  display_name: Python 3 (ipykernel)
  language: python
  name: python3
---

```{code-cell} ipython3
import numpy as np
import matplotlib.pyplot as plt
plt.style.use('fivethirtyeight')
```

# Computational Mechanics Project #01 - Heat Transfer in Forensic Science

We can use our current skillset for a macabre application. We can predict the time of death based upon the current temperature and change in temperature of a corpse. 

Forensic scientists use Newton's law of cooling to determine the time elapsed since the loss of life, 

$\frac{dT}{dt} = -K(T-T_a)$,

where $T$ is the current temperature, $T_a$ is the ambient temperature, $t$ is the elapsed time in hours, and $K$ is an empirical constant. 

Suppose the temperature of the corpse is 85$^o$F at 11:00 am. Then, 45
min later the temperature is 80$^{o}$F. 

Assume ambient temperature is a constant 65$^{o}$F.

1. Use Python to calculate $K$ using a finite difference approximation, $\frac{dT}{dt} \approx \frac{T(t+\Delta t)-T(t)}{\Delta t}$.

+++

# Question 1

```{code-cell} ipython3
Ta = 65 #temp ambient in fahrenheit
T1 = 85 #Initial temp of the corpse in fahrenheit
T2 = 80 #Final temp of the corpse in fahrenheit
dt = 45/60 #time elapsed between t1 and t2 in hours

dT = T2 - T1
k = -dT/dt/(T2 - Ta)

print('The value of K is:', k)
```

2. Change your work from problem 1 to create a function that accepts the temperature at two times, ambient temperature, and the time elapsed to return $K$.

+++

# Question 2

```{code-cell} ipython3
def measure_K(T1, T2, Ta, dt):
    '''This function returns the value of by using the finite difference approximation.
    
    Arguments
    ---------
    
    T0 = Initial temperature
    T2 = The temperature after two hours
    Ta = ambient temperature
    dt = Time elapsed
    
    
    Returns
    -------
    measure_k: the value of k'''
    
    dT = T2 - T1  #Finds the value of dt
    k = -dT/dt/(T2 - Ta)
    return k
```

```{code-cell} ipython3
T1 = 85   # initial temperature in °F
T2 = 80   # temperature after 45 min or .75 hours in °F
Ta = 65   # ambient temperature in °F
dt = 45/60    # time elapsed in hours

K = measure_K(T1, T2, Ta, dt)
print("The value of k is:", K)
```

3. A first-order thermal system has the following analytical solution, 

    $T(t) =T_a+(T(0)-T_a)e^{-Kt}$

    where $T(0)$ is the temperature of the corpse at t=0 hours i.e. at the time of discovery and $T_a$ is a constant ambient temperature. 

    a. Show that an Euler integration converges to the analytical solution as the time step is decreased. Use the constant $K$ derived above and the initial temperature, T(0) = 85$^o$F. 

    b. What is the final temperature as t$\rightarrow\infty$?
    
    c. At what time was the corpse 98.6$^{o}$F? i.e. what was the time of death?

```{code-cell} ipython3
#Analytical Solution





plt.plot(year, population, '', label='')
plt.plot(t, p_analytical, label='')
plt.xlabel('')
plt.ylabel('')
plt.legend()
plt.title('')
plt.show()





#Euleur Integration



plt.plot(year, population, '', label='')
plt.plot(t, p_analytical, label='')
plt.xlabel('')
plt.ylabel('')
plt.legend()
plt.title('')
plt.show()
```
