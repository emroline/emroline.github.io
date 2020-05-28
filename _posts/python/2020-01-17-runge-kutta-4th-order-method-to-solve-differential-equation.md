---
title: Runge Kutta 4th Order Method To Solve Differential Equation Using Python
#subtitle: "Algorithms"
#author: anuroop
categories: [ Python, Python Examples]
excerpt: "Runge Kutta method is used to integrate differential equations iteratively using computer programs. Here we will implement it using Python."
tags: [featured, Physics, Algorithms]
under_development: false
use_math: true
---

If we have following input:
* Ordinary differential equation that defines value of dy/dx in the form x and y.
* Initial value of y, ie., y(0)

Thus we have:  

$$
\frac{dx}{dy} = f(x,y)  
\\y(0) = y_0
$$

So our task is to find the value of unknown y at a given point x.

The Runge-Kutta method finds approximate value of y for a given x. Only first order ordinary differential equations can be solved by using the Runge Kutta 4th order method.

Below is the formula used to compute next value yn+1 from previous value yn. The value of n are 0, 1, 2, 3, ….(x – x0)/h. Here **h is step height** and **$$x_{n+1} = x_0 + h$$**. Lower step size means more accuracy.

$$
k_1 = hf(x_n,y_n)
\\k_2 = hf(x_n + h/2,y_n + k_1/2)
\\k_3 = hf(x_n + h/2,y_n + k_2/2)
\\k_4 = hf(x_n + h,y_n + k_3)
\\y_{n+1} = y_n + k_1/6 + k_2/3 + k_3/3 + k_4/6 + O(h^5)
$$

The formula basically computes next value $$ y_{n+1} $$ using current $$ y_n $$ plus weighted average of four increments.

$$k_1$$ is the increment based on the slope at the beginning of the interval, using y

$$k_2$$ is the increment based on the slope at the midpoint of the interval, using $$y + hk_1/2$$.

$$k_3$$ is again the increment based on the slope at the midpoint, using using $$y + hk_2/2$$.

$$k_4$$ is the increment based on the slope at the end of the interval, using $$y + hk_3$$.

The method is a fourth-order method, meaning that the local truncation error is on the order of $$O(h^5)$$, while the total accumulated error is order $$O(h^4)$$.

Sources: 
- [https://en.wikipedia.org/wiki/Runge%E2%80%93Kutta_methods](https://en.wikipedia.org/wiki/Runge%E2%80%93Kutta_methods)  
- [https://rosettacode.org/wiki/Runge-Kutta_method#Python](https://rosettacode.org/wiki/Runge-Kutta_method#Python)

Below is Python implementation for the above formula.
{% highlight python %}
{% raw %}

# Python implementation of Runge Kutta method 
# A sample differential equation "dy / dx = (x - y)/2" 
def dydx(x, y): 
    return ((x - y)/2) 
  
# Finds value of y for a given x using step size h 
# and initial value y0 at x0. 
def rungeKutta(x0, y0, x, h): 
    # Count number of iterations using step size or 
    # step height h 
    n = (int)((x - x0)/h)  
    # Iterate for number of iterations 
    y = y0 
    for i in range(1, n + 1): 
        "Apply Runge Kutta Formulas to find next value of y"
        k1 = h * dydx(x0, y) 
        k2 = h * dydx(x0 + 0.5 * h, y + 0.5 * k1) 
        k3 = h * dydx(x0 + 0.5 * h, y + 0.5 * k2) 
        k4 = h * dydx(x0 + h, y + k3) 
  
        # Update next value of y 
        y = y + (1.0 / 6.0)*(k1 + 2 * k2 + 2 * k3 + k4) 
  
        # Update next value of x 
        x0 = x0 + h 
    return y 
  
# Driver method 
x0 = 0
y = 1
x = 2
h = 0.2
print 'The value of y at x is:', rungeKutta(x0, y, x, h)   
{% endraw %}
{% endhighlight %}

The output:
{% highlight terminal %}
{% raw %}
The value of y at x is: 1.103639
{% endraw %}
{% endhighlight %}

Time Complexity of above solution is O$$(n)$$ where n is $$(x-x0)/h$$.

Some useful resources for detailed examples and more explanation.
<a href="http://w3.gazi.edu.tr/~balbasi/mws_gen_ode_txt_runge4th.pdf">http://w3.gazi.edu.tr/~balbasi/mws_gen_ode_txt_runge4th.pdf</a>

<a href="https://www.youtube.com/watch?v=kUcc8vAgoQ0">https://www.youtube.com/watch?v=kUcc8vAgoQ0</a>