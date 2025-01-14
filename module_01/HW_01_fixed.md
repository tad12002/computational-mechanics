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

> __Content modified under Creative Commons Attribution license CC-BY
> 4.0, code under BSD 3-Clause License © 2020 R.C. Cooper__

```{code-cell} ipython3
:tags: [hide-input]

import numpy as np
import matplotlib.pyplot as plt
plt.style.use('fivethirtyeight')
```

# Homework

## Problems [Part 1](./01_Interacting_with_Python.md)

1. Calculate some properties of a rectangular box that is 12.5"$\times$11"$\times$14" and weighs 31 lbs

    a. What is the volume of the box?
    
    b. What is the average density of the box?
    
    c. What is the result of the following logical operation, `volume>1000` (in inches^3)

```{code-cell} ipython3
volume = 12.5*11*14
print('Part 1, Question 1, Part A: volume of box in inches^3 is:', volume)
```

```{code-cell} ipython3
weight = 31
volume = 12.5*11*14
avg_density = weight/volume

print('Part 1, Question 1, Part B: Average desnity of the box in inches^3 is:', avg_density)
```

```{code-cell} ipython3
volume = 12.5*11*14

volume > 1000
```

```{code-cell} ipython3
print('Part 1, Question 1, Part C: The result of the following operation volume greater than a 1000 is:', volume>1000)
```

2. Use the variables given below, `str1` and `str2`, and check the following 

    a. `str1<str2`
    
    b. `str1==str2`
    
    c. `str1>str2`
    
    d. How could you force (b) to be true? [Hint](https://docs.python.org/3/library/stdtypes.html?highlight=str.lower#str.lower) or [Hint](https://docs.python.org/3/library/stdtypes.html?highlight=str.lower#str.upper)

```{code-cell} ipython3
str1 = 'Python'
str2 = 'python'

if str1 < str2:
    print('part a. str1<str2 is true')
else:
    print('part a. str1<str2 is false')
```

```{code-cell} ipython3
str1 = 'Python'
str2 = 'python'

if str1 == str2:
    print('part b. str1<str2 is true')
else:
    print('part b. str1<str2 is false')
```

```{code-cell} ipython3
str1 = 'Python'
str2 = 'python'

if str1 > str2:
    print('part c. str1<str2 is true')
else:
    print('part c. str1<str2 is false')
```

```{code-cell} ipython3
str1 = 'Python'
str2 = 'python'

str1 == str2

if str.upper(str1) == str.upper(str2):
    print('part d. str1 == str2 is true')
else:
    print('part d. str1 == str2 is false')
```

3. The following code has an error, fix the error so that the correct result is returned:

```y is 20 and x is less than y```

```python
x="1"
y=20

if x<y and y==20:
    print('y is 20 and x is less than y')
else:
    print('x is not less than y')
```

```{code-cell} ipython3
x=1
y=20

if x<y and y==20:
    print('y is 20 and x is less than y')
else:
    print('x is not less than y')
```

```{code-cell} ipython3
print('part 1, Question 3: To fix the program, to compare x and y, the x variable was noted as a string by "" and the y variable was noted as an int. So I changed the x variable to a int to fix the issue.')
```

4. There is a commonly-used programming question that asks interviewees
   to build a [fizz-buzz](https://en.wikipedia.org/wiki/Fizz_buzz) result. 
   
   Here, you will build a similar program, but use the numbers from the
   class, **3255:** $3,~2,~5\rightarrow$ "computational", "mechanics",
   "rocks!". You should print out a list of numbers, if the number is
   divisible by 3, replace the 3 with "computational". If the number is
   divisible by 2, replace with "mechanics". If the number is divisible
   by 5, replace the number with "rocks!". If the number is divisible by
   a combination, then add both words e.g. 6 is divisible by 3 and 2, so
   you would print out "computational mechanics". 
   
   Here are the first 20 outputs your program should print, 
   
| index | printed output |
| ---   | ---            |
0 | Computational Mechanics Rocks!
1 | 1
2 | Mechanics 
3 | Computational 
4 | Mechanics 
5 | Rocks!
6 | Computational Mechanics
7 | 7
8 | Mechanics 
9 | Computational 
10 | Mechanics Rocks!
11 | 11
12 | Computational Mechanics
13 | 13
14 | Mechanics 
15 | Computational Rocks!
16 | Mechanics 
17 | 17
18 | Computational Mechanics
19 | 19

```{code-cell} ipython3
import numpy as np
index = np.arange(0, 20, 1) #index list from 1-19

menderbender = []  #place holder list for when there are multiple divisble cases

fizzbuzzfinal = [] #buzz buzz


for i in index: #the divisble number list   
    if i % 3 == 0: #checking if divisible by 3
        menderbender.append('Computational')
        
    if i % 2 == 0: #checking if divisible by 2
        menderbender.append('Mechanics')
        
    if i % 5 == 0: #Checking if divisible 5
        menderbender.append('Rocks!!')
        
    if len(menderbender) == 0:
        menderbender.append(str(i))
    
    

    fizzbuzzfinal.append(''.join(menderbender))  #joins multiple divisible elements
    menderbender = [] #Resets loop
    
print(fizzbuzzfinal)
```

## Problems [Part 2](./02_Working_with_Python.md)

1. Create a function called `sincos(x)` that returns two arrays, `sinx` and `cosx` that return the sine and cosine of the input array, `x`. 

    a. Document your function with a help file in `'''help'''`
    
    b. Use your function to plot sin(x) and cos(x) for x=$0..2\pi$

```{code-cell} ipython3
print('Part 2, Question 1, a: Document your function with a help function')
```

```{code-cell} ipython3
import numpy as np
s = 0  #input starting value of range
e = 2*np.pi #input end value of range
X = np.linspace(s,e)

def sincos(X):
    '''Calculates the sin and cos of input array X as two seperate arrays, 
    one for sine of X range and one for cos of X range where the input array is defined as range specified by i.
    
    Arguments
    ---------
    i: End placeholder for array
    X: an array range specified by i
    
    Returns
    -------
    sincos: Two arrays sin(array) and cos(array)'''
    sin_array = np.sin(X)
    cos_array = np.cos(X)
    
    
    return sin_array, cos_array
    
```

```{code-cell} ipython3
sincos?
```

```{code-cell} ipython3
print('Part 2, Question 1, b: Use your function to plot sin(x) and cos(x) for x')
```

```{code-cell} ipython3
sincos(X)
```

```{code-cell} ipython3
import matplotlib.pyplot as plt

plt.rcParams.update({'font.size': 22})
plt.rcParams['lines.linewidth'] = 3

plt.plot(X, sincos(X)[0], color='b', linestyle='-', label='square')
```

```{code-cell} ipython3
import matplotlib.pyplot as plt

plt.rcParams.update({'font.size': 22})
plt.rcParams['lines.linewidth'] = 3

plt.plot(X, sincos(X)[1], color='b', linestyle='-', label='square')
```

2. Use a for-loop to create a variable called `A_99`, where every element is the product
of the two indices from 0 to 9 e.g. A_99[3,2]=6 and A_99[4,4]=16. 

    a. time your script using `%%time`    
    
    b. Calculate the mean of `A_99`

    c. Calculate the standard deviation of `A_99`

```{code-cell} ipython3
print('Part2, Question 2, a, time your script using %%time')
```

```{code-cell} ipython3
%%time

import numpy as np
thing = np.arange(0,10,1)

A_99 = []
menderbender = []


for i in thing:
    for j in thing:
        menderbender.append(i*j)
    A_99.append(menderbender)
    menderbender = []
        
A_99 = np.reshape(A_99, (10,10))
```

```{code-cell} ipython3
print('Proof this for loop above works below!')
```

```{code-cell} ipython3
import numpy as np
thing = np.arange(0,10,1)

A_99 = []
menderbender = []


for i in thing:
    for j in thing:
        menderbender.append(i*j)
    A_99.append(menderbender)
    menderbender = []
        
A_99 = np.reshape(A_99, (10,10))
print(A_99)

print(A_99[4,2] ,A_99[3,2], A_99[4,4])
```

```{code-cell} ipython3
print('Part2, Question 2, b, Calculate the mean of A_99')
```

```{code-cell} ipython3
import numpy as np
thing = np.arange(0,10,1)

A_99 = []
menderbender = []


for i in thing:
    for j in thing:
        menderbender.append(i*j)
    A_99.append(menderbender)
    menderbender = []

mean_A_99 = np.mean(A_99)



print('The mean of A_99 is:', mean_A_99 )
```

```{code-cell} ipython3
print('Part2, Question 2, c, Calculate the standard deviation of A_99')
```

```{code-cell} ipython3
import numpy as np
thing = np.arange(0,10,1)

A_99 = []
menderbender = []


for i in thing:
    for j in thing:
        menderbender.append(i*j)
    A_99.append(menderbender)
    menderbender = []

std_dev_A_99 = np.std(A_99)



print('The std deviation of A_99 is:', std_dev_A_99 )
```

3. Use the two arrays, X and Y, given below to create A_99 using numpy array math rather than a for-loop.

```{code-cell} ipython3
X, Y = np.meshgrid(np.arange(10), np.arange(10))
```

    a. time your script using `%%time`    
    
    b. Calculate the mean of `A_99`

    c. Calculate the standard deviation of `A_99`
        
    d. create a filled contour plot of X, Y, A_99 [contourf plot documentation](https://matplotlib.org/3.1.1/api/_as_gen/matplotlib.pyplot.contourf.html)

```{code-cell} ipython3
print('Part 2, Question 3, Part A: Time the script!')
```

```{code-cell} ipython3
%%time
import numpy as np
X, Y = np.meshgrid(np.arange(10), np.arange(10))
A_99 = X * Y
```

```{code-cell} ipython3
print('Part 2, Question 3, Part B: Calculate the mean of `A_99`')
```

```{code-cell} ipython3
import numpy as np
X, Y = np.meshgrid(np.arange(10), np.arange(10))
A_99 = X * Y
mean_A_99 = np.mean(A_99)

print('The mean of A_99 is:', mean_A_99 )
```

```{code-cell} ipython3
print('Part 2, Question 3, Part C: Calculate the standard deviation of `A_99`')
```

```{code-cell} ipython3
import numpy as np
X, Y = np.meshgrid(np.arange(10), np.arange(10))
A_99 = X * Y
std_dev_A_99 = np.std(A_99)

print('The std deviation of A_99 is:', std_dev_A_99 )
```

```{code-cell} ipython3
print('Part 2, Question 3, Part D: create a filled contour plot of X, Y, A_99')
```

```{code-cell} ipython3
import numpy as np
X, Y = np.meshgrid(np.arange(10), np.arange(10))
A_99 = X * Y
A_99


cs = plt.contourf(A_99, levels=[10, 30, 50],
    colors=['#808080', '#A0A0A0', '#C0C0C0'], extend='both')
cs.cmap.set_over('red')
cs.cmap.set_under('blue')
cs.changed()
```

4. The following linear interpolation function has an error. It is supposed to return y(x) given the the two points $p_1=[x_1,~y_1]$ and $p_2=[x_2,~y_2]$. Currently, it just returns an error.

```python
def linInterp(x,p1,p2):
    '''linear interplation function
    return y(x) given the two endpoints 
    p1=np.array([x1,y1])
    and
    p2=np.array([x2,y2])'''
    slope = (p2[2]-p1[2])/(p2[1]-p1[1])
    
    return p1[2]+slope*(x - p1[1])
```

```{code-cell} ipython3
print('Part 2, Question 4:')
```

```{code-cell} ipython3
print('To fix the following code, the error beign shown is "IndexError: tuple index out of range". This is referring to the p1 and p2 array. When the p2 term in the function is calling for 2, this acutally is the third term in the list rather than the second term which is y2. This is the case for all terms calling back to the array being one index ahead of the number is should be. Changing 2 to 1 and 1 to 0, the function works as it should!!')
```

```{code-cell} ipython3
def linInterp(x,p1,p2):
    '''linear interplation function
    return y(x) given the two endpoints 
    p1=np.array([x1,y1])
    and
    p2=np.array([x2,y2])'''
    slope = (p2[1]-p1[1])/(p2[0]-p1[0])

    return p1[1]+slope*(x - p1[0])

linInterp(1,(2,3),(1,4))
```

## Problems [Part 3](03_Numerical_error.md)

1. The growth of populations of organisms has many engineering and scientific applications. One of the simplest
models assumes that the rate of change of the population p is proportional to the existing population at any time t:

$\frac{dp}{dt} = k_g p$

where $t$ is time in years, and $k_g$ is growth rate in \[1/years\]. 

The world population has been increasing dramatically, let's make a prediction based upon the [following data](https://worldpopulationhistory.org/map/2020/mercator/1/0/25/) saved in [world_population_1900-2020.csv](../data/world_population_1900-2020.csv):


|year| world population |
|---|---|
|1900|1,578,000,000|
|1950|2,526,000,000|
|2000|6,127,000,000|
|2020|7,795,482,000|

a. Use a growth rate of $k_g=0.013$ [1/years] and compare the analytical solution (use initial condition p(1900) = 1578000000) to the Euler integration for time steps of 20 years from 1900 to 2020 (Hint: use method (1)- plot the two solutions together with the given data) 

b. Discussion question: If you decrease the time steps further and the solution converges, will it converge to the actual world population? Why or why not? 

**Note: We have used a new function `np.loadtxt` here. Use the `help` or `?` to learn about what this function does and how the arguments can change the output. In the next module, we will go into more details on how to load data, plot data, and present trends.**

```{code-cell} ipython3
import numpy as np
import matplotlib.pyplot as plt

year, pop = np.loadtxt('../data/world_population_1900-2020.csv',skiprows=1,delimiter=',',unpack=True)
print('years=',year)
print('population =', pop)
```

```{code-cell} ipython3
plt.plot(year,pop,'s-')
```

```{code-cell} ipython3
print('average population changes 1900-1950, 1950-2000, 2000-2020')
print((pop[1:] - pop[0:-1])/(year[1:] - year[0:-1]))
print('average growth of 1900 - 2020')
print(np.mean((pop[1:] - pop[0:-1])/(year[1:] - year[0:-1])))
```

# Numerical Integration

$\frac{dP}{dt} = kgP$

```{code-cell} ipython3
data = np.loadtxt('../data/world_population_1900-2020.csv', delimiter=',', skiprows=1)

year = data[:, 0]
population = data[:, 1]

k = 0.013  
p0 = 1578000000  


t = np.linspace(1900, 2020, 1000)
p_analytical = p0 * np.exp(k * (t - 1900))


plt.plot(year, population, 'o', label='Data')
plt.plot(t, p_analytical, label='Analytical Solution')
plt.xlabel('Year')
plt.ylabel('World Population')
plt.legend()
plt.title('World Population Growth')
plt.show()


dt = 20  
k = 0.013
t_euler = np.arange(1900, 2021, dt)
p_euler = np.zeros(len(t_euler))
p_euler[0] = pop[0]
for i in range(1,len(t_euler)):
    p_euler[i] = p_euler[i-1] + k * p_euler[i-1] * dt


plt.plot(year, population, 'o', label='Data')
plt.plot(t, p_analytical, label='Analytical Solution')
plt.plot(t_euler, p_euler, label='Euler Integration (dt=20 years)')
plt.xlabel('Year')
plt.ylabel('World Population')
plt.legend()
plt.title('World Population Growth')
plt.show()
```

```{code-cell} ipython3
print('b. If you decrease the time steps further and the solution converges, it will not necessarily converge to the actual world population. The population growth model assumes a continuous, exponential growth, but in reality, population growth is influenced by various factors that cannot be accurately captured by a simple model.')
```

__d.__ As the number of time steps increases, the Euler approximation approaches the analytical solution, not the measured data. The best-case scenario is that the Euler solution is the same as the analytical solution.

+++

2. In the freefall example you used smaller time steps to decrease the **truncation error** in our Euler approximation. Another way to decrease approximation error is to continue expanding the Taylor series. Consider the function f(x)

    $f(x)=e^x = 1+x+\frac{x^2}{2!}+\frac{x^3}{3!}+\frac{x^4}{4!}+...$

    We can approximate $e^x$ as $1+x$ (first order), $1+x+x^2/2$ (second order), and so on each higher order results in smaller error. 
    
    a. Use the given `exptaylor` function to approximate the value of exp(1) with a second-order Taylor series expansion. What is the relative error compared to `np.exp(1)`?
    
    b. Time the solution for a second-order Taylor series and a tenth-order Taylor series. How long would a 100,000-order series take (approximate this, you don't have to run it)
    
    c. Plot the relative error as a function of the Taylor series expansion order from first order upwards. (Hint: use method (4) in the comparison methods from the "Truncation and roundoff error accumulation in log-log plot" figure)

```{code-cell} ipython3
from math import factorial
def exptaylor(x,n):
    '''Taylor series expansion about x=0 for the function e^x
    the full expansion follows the function
    e^x = 1+ x + x**2/2! + x**3/3! + x**4/4! + x**5/5! +...'''
    if n<1:
        print('lowest order expansion is 0 where e^x = 1')
        return 1
    else:
        ex = 1+x # define the first-order taylor series result
        for i in range(1,n):
            ex+=x**(i+1)/factorial(i+1) # add the nth-order result for each step in loop
        return ex
approx = exptaylor(1, 2)
actual = np.exp(1)

relative_error = abs(approx - actual) / actual
print("Relative Error:", relative_error) 
```

```{code-cell} ipython3
import timeit


start_time = timeit.default_timer()
exptaylor(1, 2)
end_time = timeit.default_timer()
second_order_time = end_time - start_time


start_time = timeit.default_timer()
exptaylor(1, 10)
end_time = timeit.default_timer()
tenth_order_time = end_time - start_time


hundred_thousand_order_time = tenth_order_time * 100000 / 10

print("Second-Order Time:", second_order_time)
print("Tenth-Order Time:", tenth_order_time)
print("Estimated Hundred Thousand Order Time:", hundred_thousand_order_time)
```

```{code-cell} ipython3
import matplotlib.pyplot as plt

orders = np.arange(1, 11)  
relative_errors = []

for order in orders:
    approximation = exptaylor(1, order)
    relative_error = abs(approximation - np.exp(1)) / np.exp(1)
    relative_errors.append(relative_error)


plt.plot(orders, relative_errors, 'bo-')
plt.xlabel('Taylor Series Expansion Order')
plt.ylabel('Relative Error')
plt.title('Relative Error vs. Taylor Series Expansion Order')
plt.grid(True)
plt.show()
```

```{code-cell} ipython3
print('For all of part 3 I got totally lost. I found resoruces on your youtube explaining the first question in part 3 for the euleur approx. Followed it understood it but I dont understand how I keep getting the call back error do you have a suggestion on it becuase I ended up running into the same issue for the rest of the part and questions!')
```
