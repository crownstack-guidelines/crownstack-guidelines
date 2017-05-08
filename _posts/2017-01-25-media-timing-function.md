---
title:  "Creating a custom easing function."
date:   2017-01-25
author: Aashish Dhawan
categories:
- blog
tags:
- iOS
---

No one can deny the importance of animation in iOS. The way they enhance the UI/UX experience is unparalleled in handheld devices. If you are an iOS developer, i am pretty sure you must have used animations at least once which also makes me assume that you are familiar with `CAMediaTimingFunction`.

`CAMediaTimingFunction` gives a real world feel to your animations. For example in real life if you throw a ball it bounces, loses its speed and comes to rest after deceleration. All of this can be explained with laws of physics and can be mimicked in animations with easing functions.

Lets examine the `CAMediaTimingFunction` and try to create some custom easing functions.

`CAMediaTimingFunction` can be created using initializers
`- init(name: String)` and `- init(controlPoints: Float, Float, Float, Float)`.

The interesting one is `init(controlPoints: Float, Float, Float, Float)` which takes four float parameters. The fact is `CAMediaTimingFunction` is created using [cubic--bezier curve](https://en.wikipedia.org/wiki/B%C3%A9zier_curve) which is quite commonly used in digital drawing tools. It needs four Points to draw a curve. How the actual drawing takes place is not in the scope of this article, also there are plenty of tutorials and videos available to explain this.

Now among these 4 points one is starting point, one is end point and rest two are called control points which are responsible for the curvature of curve. In case of `CAMediaTimingFunction` start Point and end points are fixed i.e [(0,0), (1, 1)]. Now we need two control points to draw an easing function, which is exactly what `- init(controlPoints: Float, Float, Float, Float)` asking you to provide. So if we create `CAMediaTimingFunction` with `CAMediaTimingFunction(controlPoints: x1, y1, x2, y2)` we have required four points to create the cubic--bezier curve, which are [(0, 0), (x1, y1), (x2, y2), (1, 1)].

It is no surprise that default timing functions `kCAMediaTimingFunctionLinear`, `kCAMediaTimingFunctionEaseIn`, `kCAMediaTimingFunctionEaseOut`, `kCAMediaTimingFunctionEaseInEaseOut`,
`kCAMediaTimingFunctionDefault` are also created using these four points.

Lets try to find out what these control points are.

## Control points of default easing functions.

Run following code in playground

{% gist 829dfdb8ab804196520081806f7dac50 %}

This code just gets the start/end points and control points and prints them in console. You will see following log printed in playground.

```
linear
(0.00, 0.00)
(0.00, 0.00)
(1.00, 1.00)
(1.00, 1.00)

easeIn
(0.00, 0.00)
(0.42, 0.00)
(1.00, 1.00)
(1.00, 1.00)

easeOut
(0.00, 0.00)
(0.00, 0.00)
(0.58, 1.00)
(1.00, 1.00)

easeInEaseOut
(0.00, 0.00)
(0.42, 0.00)
(0.58, 1.00)
(1.00, 1.00)

default
(0.00, 0.00)
(0.25, 0.10)
(0.25, 1.00)
(1.00, 1.00)
```

Please notice that start point and end point are same for every function while control points define the behavior of the function.

## Plotting the curve.

Lets try to plot all these function to examine how they look like.

{% gist c4c32498d215e407770be8ed7151550a %}

The above code snippet creates a class `EasingFunctionGraph` which plots the function curve given the control points.

Please notice that in `let firstLine = EasingFunctionGraph(x1: 0.25, y1: 0.1, x2: 0.25, y2: 1.0)` we have passed the control points for `kCAMediaTimingFunctionDefault` which we got above. You will see following curve plotted in playground live view.

<img src="http://aashishdhawan.github.io/images/default-plot.png" alt="Drawing" style="width: 200px;"/>

Lets try `easeInEaseOut` curve with `let firstLine = EasingFunctionGraph(x1: 0.42, y1: 0.0, x2: 0.58, y2: 1.0)`. You will see following curve plotted in playground live view.

<img src="http://aashishdhawan.github.io/images/ease-in-ease-out.png" alt="Drawing" style="width: 200px;"/>


This is fun. Now we can try custom values for control points and see how this curve behaves.

Actually we can create a lot of custom curves like this

<img src="http://aashishdhawan.github.io/images/all-curves.png" alt="Drawing" style="width: 600px;"/>

There is a good cheat sheet available [here](http://easings.net/).

Lets create an extension using above cheat sheet

{% gist f91dfc1360a9c3a755d74f91c03fd30c %}

Although we can not create damping or oscillation curve with these but these additional curves are also awesome.

Happy Coding.
