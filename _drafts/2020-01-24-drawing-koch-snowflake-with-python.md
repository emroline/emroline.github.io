---
categories: [ Algorithms, ]
#excerpt: 
tags: []
under_development: false
sidebar:
    nav: "home"
---
<p class="text-center">
<img src="/assets/images/Von_Koch_curve.gif" alt="Koch Curve or Koch Snowflake">
</p>

## What is Koch Curve or Koch Snowflake?
The Koch snowflake (also known as the Koch curve, Koch star, or Koch island) is a mathematical curve and one of the earliest fractals to have been described.  It is based on the Koch curve, which appeared in a 1904 paper titled "On a Continuous Curve Without Tangents, Constructible from Elementary Geometry" by the Swedish mathematician Helge von Koch.

To know more about Koch Curve visit this <a href="https://en.wikipedia.org/wiki/Koch_snowflake">Wikipedia article</a>.

## Representation as Lindenmayer system (L-System):
An L-System is a way of representing recursive structures (such as fractals) as a string of characters, this is done by rewriting the string over and over.

The Koch curve can be expressed using <a href="https://en.wikipedia.org/wiki/L-system">L-System</a>:

* F: Move Forward
* +: Turn Right
* -: Turn Left

{% highlight python %}
{% raw %}
axiom = "F--F--F"
rules = {"F":"F+F--F+F"}
iterations = 4 # TOP: 7
angle = 60
{% endraw %}
{% endhighlight %}

To draw, here we will use Turtle module in Python standard library.

Following is the Python implementation:
{% highlight python %}
{% raw %}
import turtle
from math import cos, sin, radians

def create_l_system(iters, axiom, rules):
    start_string = axiom
    if iters == 0:
        return axiom
    end_string = ""
    for _ in range(iters):
        end_string = "".join(rules[i] if i in rules else i for i in start_string)
        start_string = end_string

    return end_string

def draw_l_system(t, instructions, angle, distance):
    steps = len([i for i in instructions if i in "FB"])
    step = 1 / steps
    i = 0
    for cmd in instructions:
        if cmd == 'F':
            t.forward(distance)
        elif cmd == 'B':
            t.backward(distance)
        elif cmd == '+':
            t.right(angle)
        elif cmd == '-':
            t.left(angle)

def calc_length_height(instructions, angle, correction_angle):
    current_angle = correction_angle
    x_offset = 0
    y_offset = 0
    min_x = 0
    min_y = 0
    max_x = 0
    max_y = 0
    for inst in instructions:
        if inst == "F":
            x_offset += cos(radians(current_angle))
            y_offset += sin(radians(current_angle))
        elif inst == "B":
            x_offset -= cos(radians(current_angle))
            y_offset -= sin(radians(current_angle))
        elif inst == "+":
            current_angle -= angle
        elif inst == "-":
            current_angle += angle
        max_x = max(max_x, x_offset)
        min_x = min(min_x, x_offset)
        max_y = max(max_y, y_offset)
        min_y = min(min_y, y_offset)
    
    width = abs(max_x) + abs(min_x)
    height = abs(max_y) + abs(min_y)


    return width, height, abs(min_x), abs(min_y)

def main(iterations, axiom, rules, angle, length=None, size=None, correction_angle=0,
        y_offset=None, x_offset=None, offset_angle=None, inverted=False, flip_h=False, 
        flip_v=False, width=None, height=None, margin=None, aspect_ratio=None):

    inst = create_l_system(iterations, axiom, rules)

    width_, height_, min_x, min_y = calc_length_height(inst, angle, correction_angle)

    if width_ == 0 and height_ == 0:
        return

    if aspect_ratio is None:
        if 0 in [width_, height_]:
            aspect_ratio = 1
        else:
            aspect_ratio = width_ / height_

    if width is None and height:
        width = height / aspect_ratio

    if height is None and width:
        height = width / aspect_ratio
    
    if margin is None:
        margin = 35

    if offset_angle is None:
        offset_angle = -90

    if length is None:
        if width_ > height_:
            length = (width - 2 * margin) / width_
        else:
            length = (height - 2 * margin) / height_
    
    if width_ * length > width:
        length = (width - 2 * margin) / width_
    elif height_ * length > height:
        length = (height - 2 * margin) / height_
    
    if x_offset is None:
        if width_ >= height_  and (width - width_) <= width_ - 2 * margin :
            x_offset = -(width / 2 - margin) + min_x * length
        else:
            x_offset = -(width / 2) + (width - width_ * length) / 2 + min_x * length
    
    if y_offset is None:
        if height_ >= width_ and (height - height_) <= height_ - 2 * margin :
            y_offset = -(height / 2 - margin) + min_y * length
        else:
            y_offset = -(height / 2) + (height - height_ * length) / 2 + min_y * length

    if inverted:
        inst = inst.replace('+', '$')
        inst = inst.replace('-', '+')
        inst = inst.replace('$', '-')
        inst = inst.replace('F', '$')
        inst = inst.replace('B', 'F')
        inst = inst.replace('$', 'B')
    
    if flip_h:
        inst = inst.replace('F', '$')
        inst = inst.replace('B', 'F')
        inst = inst.replace('$', 'B')
        y_offset *= -1

    if flip_v:
        inst = inst.replace('+', '$')
        inst = inst.replace('-', '+')
        inst = inst.replace('$', '-')
        y_offset *= -1

    if size is None:
        if length < 3:
            size = 1
        elif length < 12:
            size = 2
        elif length < 25:
            size = 3
        else:            
            size = 5

    t = turtle.Turtle()
    wn = turtle.Screen()
    wn.setup(width, height)

    t.up()    
    t.backward(-x_offset)
    t.left(90)
    t.backward(-y_offset)
    t.left(offset_angle)
    t.down()
    t.speed(0)
    t.pensize(size)
    draw_l_system(t, inst, angle, length)
    t.hideturtle()
    
    wn.exitonclick()

# Global parameters

width = 450

title = "Koch-Snowflake" 
axiom = "F--F--F"
rules = {"F":"F+F--F+F"}
iterations = 3 # TOP: 7
angle = 60

main(iterations, axiom, rules, angle, aspect_ratio=1, width=width)
{% endraw %}
{% endhighlight %}

To learn about more types of Koch Curves follow this <a href="https://elc.github.io/posts/plotting-fractals-step-by-step-with-python/">link</a>.