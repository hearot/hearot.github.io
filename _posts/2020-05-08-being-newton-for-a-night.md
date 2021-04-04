---
title: "Being Newton for a night!"
published: true
---

During the quarantine dued to the [2019-2020 Coronavirus pandemic](https://en.wikipedia.org/wiki/COVID-19_pandemic), [Isaac Newton](https://en.wikipedia.org/wiki/Isaac_Newton) came to my mind. In fact, sir Newton was quarantined as well. In August 1665 his university closed down in order to prevent the spread of the [Great Plague of London](https://en.wikipedia.org/wiki/Great_Plague_of_London). What is remarkable is that he developed his calculus and physics theories while staying at home[^1]. So my thought was: "*Am I able to experiment physics at home?*". The answer was definitely affirmative.

## Table of Contents
  - [Introduction to the pendulum](#introduction-to-the-pendulum)
  - [The pendulum viewed graphically](#the-pendulum-viewed-graphically)
  - [The experiment](#the-experiment)


## Introduction to the pendulum
{% figure caption:"*Figure 1: the physical model<br/>for an ideal pendulum.*" %}
  ![The physical model for an ideal pendulum.](https://edu.hearot.it/Experiments/Physics/Pendulum%20Motion/figure_1.png){:style="max-width: 100%; height: auto; width: 225px"}
{% endfigure %}

  A pendulum is a weight linked to a pivot by a string that freely swings.[^2] It is so interesting and apparently simple that physicists have been studying it for ages. For example, the Italian scientist [Galileo Galilei](https://en.wikipedia.org/wiki/Galileo_Galilei) designed a pendulum clock in 1641[^3], although he didn't succeed in building it. In fact, the one who built the first pendulum clock is the Dutch physicist [Christiaan Huygens](https://en.wikipedia.org/wiki/Christiaan_Huygens), who did so in 1656 and published his theory of the pendulum seventeen years later. It is worth mentioning that its deviation was around a bunch of seconds a day, which was extremely accurate by that time.[^4] It took almost 300 years to exceed its accuracy: indeed, in 1921, the quartz [crystal oscillator](https://en.wikipedia.org/wiki/Crystal_oscillator) was invented and replaced the pendulum.[^5]

  One of the most studied physical models about the pendulum is the one which interacts with [gravity](https://en.wikipedia.org/wiki/Gravity) and assumes no [air resistance](https://en.wikipedia.org/wiki/Drag_(physics)) (see *Figure 1*). By simply summing up all the information, it is possible to obtain a flexible system of equations:

  $$\begin{cases}
    ma_c=|\vec{T}|-mg\cos(\theta) \\
    ma_t=-mg\sin(\theta)
  \end{cases}$$

  where $m$ stands for the mass of the weight, while $a_c$ and $a_t$ represent respectively the [centripetal and the tangential acceleration](https://en.wikipedia.org/wiki/Acceleration#Tangential_and_centripetal_acceleration). It is worth noting that the positive horizontal direction is assumed to be opposite to the direction of the weight and that the vertical one follows the [tension](https://en.wikipedia.org/wiki/Tension_(physics)). From the second equation it follows the $a_t=-g\sin(\theta)$.

  In particular $a_t$ can be written as $\ddot\theta \ell$, where $\ell$ stands for the length of the linking string. Thus, the second equation is revealed to be the [differential equation](https://en.wikipedia.org/wiki/Differential_equation) $\ddot\theta \ell=-g\sin(\theta)$.

  On the other hand, $\sin(\theta)$ can be replaced with its own [Maclaurin series](https://en.wikipedia.org/wiki/Taylor_series), which is $\displaystyle \theta-\frac{\theta^3}{6}+\frac{\theta^5}{120}-\frac{\theta^7}{5040}+\dots$

  Hence, it follows that $\sin(\theta)\approx\theta$ for very small values of $\theta$ in [radians](https://en.wikipedia.org/wiki/Radian). This is actually a direct consequence of the value of the limit $\displaystyle \lim_{\theta \to 0}\frac{\sin(\theta)}{\theta}$ being equal to $1$.

  Therefore, it is sufficient to resolve the differential equation $\ddot\theta \ell=-g \theta$. Substituting $\theta=e^{\lambda t}$, we get to resolve the [characteristic equation](https://en.wikipedia.org/wiki/Linear_difference_equation#Characteristic_equation_and_roots) $\lambda^2\ell=-g$, whose complex roots are $\pm i\sqrt{\frac{g}{\ell}}$.

  As a result, the general form for $\theta(t)$ is $A\cos(\sqrt{\frac{g}{\ell}}t)+B\sin(\sqrt{\frac{g}{\ell}}t)$. According to the fact that the initial [angular velocity](https://en.wikipedia.org/wiki/Angular_velocity) is zero (i.e. $\dot\theta(0)=0$), $B$ must be equal to zero as well.  

  Finally, $\theta(t)$ can now be written in the form $A\cos(\sqrt{\frac{g}{\ell}}t)$, which is a function of period $T=2\pi\sqrt{\frac{\ell}{g}}$, whose maximum value is the initial amplitude $A$.

## The pendulum viewed graphically

  After having found the general equation that describes the pendulum motion for small angles, I created a simple script in [Python](https://en.wikipedia.org/wiki/Python_(programming_language)) using [Matplotlib](https://en.wikipedia.org/wiki/Matplotlib) and [NumPy](https://en.wikipedia.org/wiki/NumPy):

  <script src="https://gist.github.com/hearot/06c48e9a9c6ff81e9dea6e2a22e05ec2.js"></script>

{% figure caption:"*Figure 2: the pendulum<br/>motion over time.*" %}
  ![The pendulum motion.](https://edu.hearot.it/Experiments/Physics/Pendulum%20Motion/figure_2.gif){:style="max-width: 100%; height: auto; width: 225px"}
{% endfigure %}

  I thereupon executed it and plotted the function $\theta(t)$ (see *Figure 2*). As we can see, the plot is actually a [sinusoid](https://en.wikipedia.org/wiki/Sine_wave), which respects all the conditions we assumed while trying to retrieve a general form for the pendulum equation.

  In fact, at $t=0$, we get the maximum value of the function (i.e. the initial amplitude $A$), but we still get this value if we increment the time by a multiple of the period $T$.

  What is notable is the fact that the amplitude does not influence the period of the function, which in the first place might sound counterintuitive.

{% figure caption:"*Figure 3: demonstration of the<br/>independence of the period by<br/>letting the amplitude change.*" %}
  ![Demonstration of the independence of the period.](https://edu.hearot.it/Experiments/Physics/Pendulum%20Motion/figure_3.gif){:style="max-width: 100%; height: auto; width: 225px"}
{% endfigure %}

  The only variable that influences the period is the length of the linking string, while the amplitude defines the maximum achievable angle.

  Then, if we let the amplitude vary (see *Figure 3*), the value of the period does not change. That is because if we increase the amplitude, the gravity force makes the weight achieve more speed, which compensates the variation.

  The weight does not stop either because of the [law of inertia](https://en.wikipedia.org/wiki/Newton%27s_laws_of_motion#Newton's_first_law), which guarantees the continuity of the motion.

  As a result of all these combinations of information, it follows that neither the mass influences the period. Actually, the mass is insignificant for the whole physical system except for the tension.

{% figure caption:"*Figure 4: pendulum<br/>velocity over time.*" %}
  ![Pendulum velocity over time.](https://edu.hearot.it/Experiments/Physics/Pendulum%20Motion/figure_4.gif){:style="max-width: 100%; height: auto; width: 225px"}
{% endfigure %}

  Even the velocity plot (see *Figure 4*) shares the same period as the motion one. That is because the first derivative of $\theta(t)$ (i.e. the velocity itself) is equal to $-\sqrt{\frac{g}{\ell}}A\sin\(\sqrt{\frac{g}{\ell}}t\)$, whose period is identical to the one of the motion.

  At the $t=0$, just as we assumed it to be, the velocity is equal to zero, while the maximum speed is obtained each half of the period $T$ starting from $t=\frac{T}{4}$, which happens when the weight is perpendicular to the plane (i.e. $\theta(t)=0$).

  Indeed, the maximum speed is equal to $\left\lvert \dot \theta(\frac{T}{4}) \right\rvert$, which can be expanded to be equivalent to $A\frac{2\pi}{T}$.

  Although we've found these magnificent results, it must be remembered that all these formulas tend to work if and only if the air resistance is assumed not to exist and the amplitude is much less than $1$.

## The experiment

{% figure caption:"*Figure 5: the measurement of<br/>the string of the yo-yo.*" %}
  ![The measurement of the string of the yo-yo.](https://edu.hearot.it/Experiments/Physics/Pendulum%20Motion/figure_5.jpg){:style="max-width: 100%; height: auto; width: 225px"}
{% endfigure %}

  Having the pendulum motion been explained, I thought it would be awesome to experiment it in real life. Therefore, I seeked an object whose motion could be comparable to the pendulum one.

  All I found was a [yo-yo](https://en.wikipedia.org/wiki/Yo-yo), which is pretty similar to a pendulum, but I didn't find anything to reduce the air resistance at all. Then, I took a meterstick and I measured the length of the string, which was about $90\text{ cm}$ (see *Figure 5*).

  Actually, it is enough: we can already predict the value of the period. I subsequently calculated the period $T$ and it turned out to be about $1.90345\text{ s}$.
  
{% figure caption:"*Figure 6: the yo-yo motion<br/>caught during the experiment.*" %}
  ![The yo-yo motion caught during the experiment.](https://edu.hearot.it/Experiments/Physics/Pendulum%20Motion/figure_6.gif){:style="max-width: 100%; height: auto; width: 225px"}
{% endfigure %}

  I could have weighed the yo-yo, but I did not for a simple reason: it does not matter. In fact, the weight doesn't appear anywhere in our equations.

  What I did was take my stopwatch and prepare to measure the period of the motion (see *Figure 6*). After having taken all the measurements, I calculated the arithmetic mean. It turned out to be approximately $1.872\text{ s}$.

  Actually, I was surprised: the difference between the value I calculated and the one I got by rearranging my measurements was just $0.03145\text{ s}$!

  Hence, we can conclude that the equations we found are revealed to be producing correct results.

  Although I did not mention it earlier, the physical system we've been analysing during the experiment can be generalised using the [simple harmonic motion](https://en.wikipedia.org/wiki/Simple_harmonic_motion) equations. It follows that the pendulum behaviour is approximately the same as a [harmonic oscillator](https://en.wikipedia.org/wiki/Harmonic_oscillator) for small angles. This implies that a pendulum behaves like a [spring](https://en.wikipedia.org/wiki/Spring_(device)), which apparently seems not to be related to it.

  You might accuse me of retrieving equations that work just for a small range of angles, but what hasn't been said yet is that, in fact, there does not exist an elementary equation which describes the pendulum motion for all angles. Even if it did exist, it didn't matter for the experiment I performed as I had not chosen an angle either.

  The conclusion is that, even in quarantine, we are all able to prove simple physical facts, which apparently might seem to be obvious, but are actually described in a very complex way. *Newton, we did it!*

<hr/>

[^1]: Westfall, R. S. (1993). *The Life of Isaac Newton*. Cambridge University Press.
[^2]: Pendulum. (n.d.). In *Cambridge Dictionary*. Retrieved from [dictionary.cambridge.org/...](https://dictionary.cambridge.org/dictionary/english/pendulum)
[^3]: Johnstone, A. (2009, July 8). *Galileo and the pendulum clock*. Retrieved from [www.cs.rhul.ac.uk/...](http://www.cs.rhul.ac.uk/~adrian/timekeeping/galileo/)
[^4]: Mahoney, M. S. (1980). *Christian Huygens: The Measurement of Time and of Longitude at Sea*. Retrieved from [www.princeton.edu/...](https://www.princeton.edu/~hos/Mahoney/articles/huygens/timelong/timelong.html)
[^5]: Marrison, W. A. (1948). *The evolution of the quartz crystal clock*. *The Bell System Technical Journal*, vol. 27, no. 3, pp. 510-588. Retrieved from [web.archive.org/...](https://web.archive.org/web/20110717061023/http://www.ieee-uffc.org/main/history.asp?file=marrison)
