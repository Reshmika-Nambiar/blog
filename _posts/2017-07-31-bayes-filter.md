---
layout: post
title: Bayes' Filter Explained! - Part 1 - Bayes' Theorem
tags: probabilistic-robotics
description: Understand Bayes' filter.
---

-- [Saurabh Gupta](https://github.com/saurabh1002)

<img src="https://crucialconsiderations.org/wp-content/uploads/2015/06/bayes3x2.jpg" alt="bayes filter" /> 

You may have heard your friends, colleagues, and teachers talking about something called "Bayes' Theorem" or "Bayes' Rule", or something called Bayesian reasoning. They sound really enthusiastic about it, too, so you google and find a web page about Bayes' Theorem and...

It's that equation up top. That's all. Just one equation. Most of you must also have written exams in high school testing how well you remember this equation. But most of you have only studied a definition of it, but don’t understand what it is, or why it's useful, or why your friends would be interested in it. Today, let's dive a little deep and try to understand intuitively what actually Bayes Theorem signifies.

**Before jumping to the Bayes Rule, let us recap some of the important concepts in Probability Theory:**

We will go through the concepts of probability theory by considering a simple example. Imagine we have two boxes, one red and one blue, and in the red box we have 2 apples and 6 oranges, and in the blue box, we have 3 apples and 1 orange.

Now suppose we randomly pick one of the boxes and from that box, we randomly select an item of fruit and having observed which sort of fruit it is we replace it in the box from which it came. Let us suppose that in so doing we pick the red box 40% of the time and we pick the blue box 60% of the time and that when we remove an item of fruit from a box we are equally likely to select any of the pieces of fruit in the box. Suppose we repeat this process many times over.

Hence, the identity of the box that will be chosen is a discrete _random variable_, which we shall denote by B. It can take two values, namely _r_ (red box) or _b_ (blue box). Similarly, the identity of the fruit is also a discrete _random variable_ and will be denoted by F. It can take either of the values _a_ (for apple) or _o_ (for orange).

To begin with, we shall define the probability of an event to be the _fraction of times that event occurs out of the total number of trials, in the limit that the total number of trials goes to infinity_. This is also referred to in Probability Theory as the [Law of Large Numbers](https://en.wikipedia.org/wiki/Law_of_large_numbers)(LLN). Thus the probability of selecting the red box i.e p(B = r) is 4/10 and the probability of selecting the blue box i.e. p(B = b) is 6/10.

Now, knowing the probability of the above two events, we can ask questions like “what is the overall probability that the selection procedure will pick an apple?”, or “given that we have chosen an orange, what is the probability that the box we chose was the blue one?”. To answer these kinds of questions, we must first understand the two important concepts in Probability Theory, namely, the _Sum Rule_ and the _Product Rule_.

Consider a grid of size M rows and L columns. Let X and Y be two random variables such that X can occupy any of the M columns and Y can occupy any of the L rows. Now we will sample X and Y for N trials. Let n<sub>ij</sub> be the number of trials out of N in which X = x<sub>i</sub> and Y = y<sub>j</sub>. Also, let c<sub>i</sub> be the number of trials in which X = x<sub>i</sub> and r<sub>j</sub> be the number of trials in which Y = y<sub>j</sub>. It is illustrated in the figure below. 

Now the _Joint Probability_ of the random variables X and Y such that X takes the value x<sub>i</sub> and Y takes the value y<sub>j</sub> is given as:

**P(X, Y) =  P(X = x<sub>i</sub> , Y = y<sub>j</sub>) = n<sub>ij</sub> / N                →                (1)**

Note: Again we assume N → ∞ for the ratios to converge towards the actual probability according to the Law of Large Numbers.

The Independent probability of X assuming the value xi is → **P(X = x<sub>i</sub>) = c<sub>i</sub> / N                →                  (2)**

 and of Y assuming the value yj is → **P(Y = y<sub>j</sub>) = r<sub>j</sub> / N                →                 (3)**

From the figure above, you can easily understand that P(X = x<sub>i</sub>) can be written as a sum of P(X, Y) over all values of Y. This is because of the fact that c<sub>i</sub> = ∑<sub>j</sub>n<sub>ij</sub>. The same is applicable to P(Y = y<sub>j</sub>).

**This simple concept is referred to as the _Sum Rule_ of probability.**

P(X = x<sub>i</sub>) is sometimes called the **_marginal probability_** because it is obtained by marginalizing, or summing out, the other variables (in this case Y ).

Now, in the above case, the outcome of both variables was unknown. Suppose, if we are given the exact outcome of any one variable i.e. let X = x<sub>i</sub>. Therefore, all the possible outcomes of Y will now be contained in the i<sup>th</sup> column i.e the maximum no. of samples that can be drawn with X = x<sub>i</sub> is c<sub>i</sub>. Hence the probability of Y assuming a value y<sub>j</sub> given that X = x<sub>i</sub> is given as:

**P(Y = yj | X = x<sub>i</sub>) = nij / c<sub>i</sub>        →        (4)**

Using Equations (1), (2) and (4) we can write P(X, Y) as follows:

**P(X = x<sub>i</sub> , Y=y<sub>j</sub>) = n<sub>ij</sub> / N = (n<sub>ij</sub> / c<sub>i</sub>) * (c<sub>i</sub> / N)**

**Therefore →  P(X, Y) = P(Y | X) * P(X)        →        (5)**

**This is the _Product Rule_ in Probability Theory.**

The product rule can be interpreted as follows:

_We want both 𝑥 and 𝑦. What if I already have 𝑦, what is the probability that I also have 𝑥? And then since we assumed we had 𝑦, we want to multiply by its probability._

_For example, say I roll a dice, and 𝑥 is getting an even number, 𝑦 is getting 4,5 or 6. I want the probability of having x and y, namely having 4 or 6. I first suppose that I have gotten y to be 4,5 or 6. Then 𝑃(𝑥|𝑦) = ⅔. But this is valid only if I get 4,5 or 6, which happens with probability 3/6 i.e. ½._

_The idea is to try to simplify a probability by assuming a portion of the randomness (in this case assuming the outcome of y). When you multiply by 𝑃(𝑦), you remove that assumption bringing back all the randomness that was present._

The above definition of Product Rule is valid for Dependent events only. In case the two events are independent, then → P(X, Y) = P(X) * P(Y). This is because knowing one quantity does not reveal anything about the other one i.e. P(X | Y) = P(X).

Up till now, we have gathered some knowledge about the two basic rules of Probability which are mentioned below:

<img src="https://datastoriesweb.files.wordpress.com/2017/06/p1.png?w=636" alt="bayes sum and product rules" />

where,

**P(X, Y) = P(Y, X)    →    Joint Probability of X and Y**

**P(X | Y)    →    Probability of X, given Y**

**P(X)    →    Probability of X or Marginal Probability of X**

Now, using the product rule, we can represent the joint probability of two variables as follows:

**P(X, Y) = P(Y | X) * P(X) = P(X | Y) * P(Y)**

**∴ P(Y | X) = ( P(X | Y) * P(Y) ) / P(X)**

**This relationship between the two conditional Probabilities P(X | Y) and P(Y | X) is called the Bayes’ Theorem.**

The denominator can be further modified using the sum and product rules as follows:

P(X) = Σ<sub>y</sub> P(X, Y) = Σ<sub>y</sub> P(X | Y) * P(Y)

**∴ P(Y | X) = ( P(X | Y) * P(Y) ) / ( Σ<sub>y</sub> P(X | Y) * P(Y) )**

The denominator can be seen as a normalizer such that the summation of the LHS over all values of Y equals one.

Let us now return to our example involving boxes of fruit.

**P(B = r) = 4 / 10**

**P(B = b) = 6 / 10**

Now suppose that we pick a box at random, and it turns out to be the blue box. Then the probability of selecting an apple is just the fraction of apples in the blue box which is ¾, and so P(F = a | B = b) = ¾. In fact, we can write out all four conditional probabilities for the type of fruit, given the selected box:

**P(F = a | B = r)  =  ¼**

**P(F = o | B = r)  =  ¾**

**P(F = a | B = b)  =  ¾**

**P(F = o | B = b)  =  ¼**

We can now use the sum and product rules of probability to evaluate the overall probability of choosing an apple.

**P(F = a)  =  P(F = a | B = r) P(B = r) + P(F = a | B = b) P(B = b)  =  (¼ * 4/10) + (¾ * 6/10)  =  (11 / 20)**

**∴ P(F = o)   =   (9 / 20)**

Suppose instead we are told that a piece of fruit has been selected and it is an orange, and we would like to know which box it came from. This is a problem of reversing the conditional probability which can be done using the Bayes’ Theorem.

**P(B = r | F = o)   =   P(F = o | B = r) * P(B = r) / P(F = o)   =   3/4 * (4 / 10) / (9 / 20)   =   2/3**

An important interpretation of the Bayes Theorem is as follows:

If we had been asked which box had been chosen before being told the identity of the selected item of fruit, then the most complete information we have available is provided by the probability p(B). We call this the _**Prior Probability** (You will hear this word a lot as you further study about Probabilistic Robotics; get familiar with it)_ because it is the probability available _before_ we observe the identity of the fruit. Once we are told that the fruit is an orange, we can then use Bayes’ theorem to compute the probability P(B | F), which we shall call the _**Posterior Probability** (get familiar with this too)_ because it is the probability obtained _after_ we have observed F. Note that in this example, the prior probability of selecting the red box was 4/10, so that we were more likely to select the blue box than the red one. However, once we have observed that the piece of selected fruit is an orange, we find that the posterior probability of the red box is now 2/3 so that it is now more likely that the box we selected was, in fact, the red one. This result accords with our intuition, as the proportion of oranges, is much higher in the red box than it is in the blue box, and so the observation that the fruit was an orange provides significant evidence favoring the red box. In fact, the evidence is sufficiently strong that it outweighs the prior and makes it more likely that the red box was chosen rather than the blue one.

So far we have studied a basic view of Bayes’ theorem and Probability in terms of the frequencies of the random, repeatable variable, which is the classical or frequentist approach. Consider the following example for a more general Bayesian view in which probabilities quantify the uncertainty in the outcome of the events.

Consider an uncertain event, for example, whether the moon was once in its own orbit around the sun, or whether the Arctic ice cap will have disappeared by the end of the century. These are not events that can be repeated numerous times in order to define a notion of probability as we did earlier in the context of boxes of fruit. Nevertheless, we will generally have some idea, for example, of how quickly we think the polar ice is melting. If we now obtain fresh evidence, for instance from a new Earth observation satellite gathering novel forms of diagnostic information, we may revise our opinion on the rate of ice loss. Our assessment of such matters will affect the actions we take, for instance, the extent to which we endeavour to reduce the emission of greenhouse gasses. In such circumstances, we would like to be able to quantify our expression of uncertainty and make precise revisions of uncertainty in the light of new evidence, as well as subsequently to be able to take optimal actions or decisions as a consequence. This can all be achieved through the elegant, and very general, Bayesian interpretation of probability.

----

## Analogy to Robotics

In the field of Robotics, consider an analogous example of keeping track of the position of the robot in relation to its surrounding. Here, the Prior Probability is based upon the motion commands given to the robot with respect to its last known position. The Posterior Probability is then calculated after making an observation of the surroundings using sensors like Laser Range finders, Infrared sensors, camera, etc.

**Why do we need a probabilistic representation of these quantities?**

It is because we cannot exactly model the execution of the motion commands. There is always some uncertainty in the actual execution of the commands (due to some difficult to model phenomenon like in-place rotation of wheels). 

Also, the sensors we use for observing the environment do not provide exact data. There is some uncertainty/noise induced in the measurement due to factors like loss of resolution in analog-to-digital conversion, cross-talk, electromagnetic interference, etc. Hence, the measurement is also represented in terms of a Probability Distribution.

**Next in this Series**, we will be discussing **Gaussian Distributions and The Kalman Filter**.

**Further Reading:**

1. [http://yudkowsky.net/rational/bayes/](http://yudkowsky.net/rational/bayes/) → An intuitive and interactive explanation of Bayes’ Rule **(A MUST READ)**
2. [Law of Large Numbers](https://en.wikipedia.org/wiki/Law_of_large_numbers)
3. Chapter 6 From Mathematics for Machine Learning: [https://github.com/mml-book/mml-book.github.io/blob/master/book/mml-book.pdf](https://github.com/mml-book/mml-book.github.io/blob/master/book/mml-book.pdf)

And to all those who read this post to the end..

<img src="https://cdn-images-1.medium.com/max/1600/1*9r-HXE9UfPdMknHzqxatGg.jpeg" alt="bayes filter finish" /> 

_**- Saurabh Gupta**_
