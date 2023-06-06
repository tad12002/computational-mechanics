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
dt_k = 45/60 #time elapsed between t1 and t2 in hours

dT = T2 - T1
k = -dT/dt_k/(T2 - Ta)

print('The value of K is:', k)
```

2. Change your work from problem 1 to create a function that accepts the temperature at two times, ambient temperature, and the time elapsed to return $K$.

+++

# Question 2

```{code-cell} ipython3
def measure_K(T1, T2, Ta, dt_k):
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
    k = -dT/dt_k/(T2 - Ta)
    return k
```

```{code-cell} ipython3
T1 = 85   # initial temperature in °F
T2 = 80   # temperature after 45 min or .75 hours in °F
Ta = 65   # ambient temperature in °F
dt_k = 45/60    # time elapsed in hours

K = measure_K(T1, T2, Ta, dt_k)
print("The value of k is:", K)
```

3. A first-order thermal system has the following analytical solution, 

    $T(t) =T_a+(T(0)-T_a)e^{-Kt}$

    where $T(0)$ is the temperature of the corpse at t=0 hours i.e. at the time of discovery and $T_a$ is a constant ambient temperature. 

    a. Show that an Euler integration converges to the analytical solution as the time step is decreased. Use the constant $K$ derived above and the initial temperature, T(0) = 85$^o$F. 

    b. What is the final temperature as t$\rightarrow\infty$?
    
    c. At what time was the corpse 98.6$^{o}$F? i.e. what was the time of death?

+++

# Question 3, Part A

```{code-cell} ipython3
# Define the parameters
T0 = 85 # initial temperature in °F
Ta = 65 # ambient temperature in °F

t_final = 10 # final time in hours
N = 50 #number of time steps

t = np.linspace(0,t_final,N)
delta_time = np.diff(t)


# Define the analytical solution
def analytical_sol(T1, Ta, K, t):
  return Ta + (T1 - Ta) * np.exp(-K * t)

T_analytical = analytical_sol(T0, Ta, K, t)

# Define the Euler integration method
def euler_integration(T0, Ta, K, delta_time, N):
  T_numerical = np.zeros(N)
  T_numerical[0] = T0
  for i in range(N-1):
    T_numerical[i+1] = T_numerical[i] + delta_time[1] * (-K * (T_numerical[i] - Ta))
  return T_numerical

T_euler = euler_integration(T0, Ta, K, delta_time, N)


plt.loglog(t,T_euler,'o',label=str(N)+' Euler steps')
plt.loglog(t,T_analytical,label='analytical')
plt.title('Euler Integration Solution vs. Analytical Solution')
plt.xlabel('time (hours)')
plt.ylabel('Temperature (f)')
plt.legend()

plt.show()
```

# Question 3, Part b

```{code-cell} ipython3
# Define the parameters
T0 = 85 # initial temperature in °F
Ta = 65 # ambient temperature in °F
t_final = 10 # final time in hours
N = 100 #number of time steps

t = np.linspace(0,t_final,N)
delta_time = np.diff(t)


# Define the analytical solution
def analytical_sol(T1, Ta, K, t):
  return Ta + (T1 - Ta) * np.exp(-K * t)

T_analytical = analytical_sol(T0, Ta, K, t)

# Define the Euler integration method
def euler_integration(T0, Ta, K, delta_time, N):
  T_numerical = np.zeros(N)
  T_numerical[0] = T0
  for i in range(N-1):
    T_numerical[i+1] = T_numerical[i] + delta_time[1] * (-K * (T_numerical[i] - Ta))
  return T_numerical

T_euler = euler_integration(T0, Ta, K, delta_time, N)

for f in T_euler:

    print(f)
```

```{code-cell} ipython3
t = float('inf')
T_analytical = Ta + (T1 - Ta) * np.exp(-K * t)

print('Final temperature as t approaches infinity: {:5.2f}'.format(T_analytical))
```

As you can see increasing the number of steps makes it so that you approach the ambient temperature value. Therefore as t approaches infinity the temperature will result in ambient and in this case ambient is 65 degrees faranheight.

+++

# Question 3, Part c

```{code-cell} ipython3
Ta = 65  # Ambient temperature in °F
T0 = 85  # Initial temperature in °F
T_desired = 98.6  # Desired temperature in °F

# Calculate the time of death when the corpse temperature reaches 98.6°F
t_death = (np.log(T0 - Ta) - np.log(T_desired - Ta)) / k

print('Time of death: {:5.4f} hours'.format(t_death))
```

```{code-cell} ipython3

```
