---
layout: post
title:  "Why are monads confusing - musings on jargon, monads and types"
date:   2019-10-04 07:43:23 +0200
categories: functional-programming categorical-programming scala monads
---

For such a simple programming pattern, monads seem to generate a lot
of confusion. With FP-beginners they cause endless discussions and
long explanation sessions. For people who do understand the topic,
"_they immediately lose the ability to explain it to others_". They
can probably even evoke a sense of intellectual elitism being directed
towards the uninitiated, along with the rest of the categorical programming
jargon.

As someone who does OOP Scala for a living, and for fun occasionally
reads a tutorial on Haskell, I've had my share of confusion. The cause
of it, I think, is a mix-and-match of different perspectives and
paradigms that are tossed around when talking about programming and
category theory, which are not neccessarily connected to their
technical use.

# Musings on monads from different perspectives

## 1 The Grease Monkey perspective

A monad is something you can put in a for-comprehension.

{% highlight scala %}

  import monad.Monad;
  
  for {
    x <- Monad(123)
    y <- Monad("4")
    z <- Monad(true)
  } yield {
    s"$x > $y = $z"
  }

{% endhighlight %}

##

{% highlight scala %}

  class Box[X](x: X) implements Monad[X] {
    // Just an alias for the constructor
    override def pure[A](a: A) = new Box(a)
    
    override def flatMap[X,Y](f: X => Monad[Y]): Monad[B] =  
  }

{% endhighlight %}

# A monad is _just a monoid in the category of endofunctors..._

I've studied CS and mathematics, so I'm very much used to abstract
words and structures, but this has nothing to do with programming.