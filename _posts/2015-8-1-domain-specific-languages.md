---
layout: post
title: "Domain Specific Languages"
author: "Auke Hoekstra"
date: "1 augustus 2015"
backgrounds: 
thumb: /pics/john-chambers-thumb.jpg
categories: DSL, computer language, markdown, LaTeX
tags: home work office coding design
---
**I would like to argue that all languages are domain specific languages and that using a combination of the right domain specific languages simplifies life and increases productivity. I'll try to make my point using three examples: first R, then Netlogo/GAML and finally a workflow using markdown, LaTeX, R and HTML.**

## Every language is Domain Specific
The term general purpose language is misleading. It creates the impression that you we can have *"one language to rule them all"* to paraphrase Tolkien. And I've noticed that many programmers hope this is possible so they don't have to learn other languages. This is problematic because firstly there is no such thing as a general purpose language and secondly it is often simpler to learn and use multiple domain specific languages when they are the right tools for the job. Let's start with the first point.

If we talk about "general purpose" we usually mean general purpose [computer languages](https://en.wikipedia.org/wiki/Programming_language) which indicates they are not really general purpose at all. Then it turns out we have "general purpose" [programming languages](https://en.wikipedia.org/wiki/General-purpose_programming_language) (like C, Java and Julia), [modeling languages](like UML and XML) and [markup languages](https://en.wikipedia.org/wiki/General-purpose_markup_language) (like markdown, LaTex, YAML and *again* XML). So we have "general purpose"" languages for "specific domains"? It indicates that it is impossible to define in absolute terms whether a language is general purpose or domain specific.

Which brings me to my second point: we get a more fruitful discussion if we simply ask ourselves: "What combination of tools gets the job done most efficiently?" It is useless to debate whether a hammer is a *general purpose* or *domain specific* tool but it sure is a better way to drive in a nail than a screwdriver. That is what the rest of this post is about.

## The example of R
A good example of unnecessary confusion is the difference in terminology between John Chambers and Hadley Wickham regarding R.

John (photo above) created the S language on which the R language is based and he claims empathically that it is **not** a general purpose language but only an interface language. Hadley on the other hand created many of the most used packages in R (together called the Hadleyverse) and claims empathically that it **is** a general purpose language on top of which you can create domain specific language. I would argue they are both right from their point of view. It simply illustrates that the term is general purpose language is meaningless.

John Chambers looks at how the computer does it's mathematical calculations (e.g. matrix multiplication) and observes that the speed increase is enormous if you do that in Fortran, C, C++ or another "general purpose" language. He only invented S (and indirectly R) so it could easily call on packages written in those other languages. The picture below illustrates the concept: the low level program is the circle which is packaged into a quadrant that is a lego piece for R. 

![](/Pics/xabc-john-chambers.png)

Hadley Wickham (photo below) agrees with this but takes the next step. He makes the language itself better by adding domain specific functions that improve R's visualisation and data wrangling capabilities. So Hadleys starting point is an abstraction layer higher. John build a layer for a specific application on top of languages like C (which makes those languages by definition relatively generic) and Hadley builds a layer on top of R (which makes R by definition relatively generic).

![Hadley with the chinese translation of his book ggplot2, courtesy of Yixuan](/pics/hadley-wickham-ggplot2-chinese.jpg)

John had the insight that he could create an interface language that was much better suited for calling packages than the lower level languages in which the packages themselves where written. This combined with the ease in which you can write and use packages makes R a real productivity booster. Hadley improves on this by adding commands that make visualising and wrangling data easier. And of course there are many others who are improving R with either new low level calculation to call on or new human productivity enhancements. I especially like the magrittr package that give R a forward pipe operator (e.g. well known in F#) which replaces nested and confusing programming with linear and straightforward programming.

Lets close with a super simple little demo of how this makes you more productive. First imagine a [C# program](http://fsharpforfunandprofit.com/posts/fvsc-sum-of-squares/) that writes a function SumSquares that gives you the sum of the squares of a list of integers from 1 to the number you enter:


{% highlight r %}
public static class SumSquaresHelper
{
   public static int Square(int i)
   {
      return i * i;
   }

   public static int SumSquares(int n)
   {
      int sum = 0;
      for (int i = 1; i <= n; i++)
      {
         sum += Square(i);
      }
      return sum;
   }
}
{% endhighlight %}

Simple right? Well here's how you can do this in R:


{% highlight r %}
SumSquares <- function(n) sum((1:n)^2)
{% endhighlight %}

## The example of Java, Netlogo & GAML
I work at the Technical University of Delft in a department that does a lot of agent based modeling. If you want to make simple models quickly you use Netlogo with its simple domain specific language. If you want to work together on larger models you use agentspring or another Java based framework. But I am intriqued by the claim of many Netlogo programmers that they can build models 10 to 20 times faster in Netlogo than Java. That seems like a big deal to me.

I think agent based programming in Netlogo instead of Java is analogous to data analysis in R instead of C. However, Netlogo has many flaws. E.g. it only works with a simple grid spatially and it has no multi-level agent definition with inheritance. It is also locked into an IDE that is simple but also rigid and a bit behind the times. 

That is why I'm exited about the language [GAML](https://code.google.com/p/gama-platform/wiki/G__GamlLanguage) and the corresponding tool [GAMA](https://code.google.com/p/gama-platform/). In many ways it is like Netlogo: an agent oriented (some would say domain specific) language that makes you drastically more productive in this domain. But it got rid of most of the aforementioned flaws in Netlogo: using GIS data and making agents use them (e.g. travel along roads) is native; agents are potentially multi-level constructs with inheritance; it is build in Java and easy to extend with plug-ins; and it uses Eclipse as an IDE. I think GAML is another good example of a domain specific language that makes you much more productive.

## markup, $$\LaTeX$$, $$\textsf{R}$$ & HTML
I want to close with a quick example of mixing domain specific languages (more details in other posts).

HTML is a very efficient and transparent markup language. E.g. Microsoft [Word needs 20x as many bytes](http://ben.balter.com/2014/03/31/word-versus-markdown-more-than-mere-semantics/) to store the same information in a way that is not human readable. But for a writer the amount of tags is still pretty distracting: a regular HTML page easily contains 20x as much tags as actual written text.

If writing is your objective you are much better off using LaTeX: you can easily specify complex formula's and other markup that even experienced HTML programmers would usually not code by hand. And although you can use a WYSIWYG (what you see is what you get) editor you can also look at the raw text without losing sight on your text. Still: do you want to type /$ everytime you mean $? Do you want to write \tesxtsc{} everytime you want to make something italic? 

In my opinion markdown is much better for normal writing: less work and it looks very natural when you see the plain text. E.g. to get *italic* you simply write `*italic*`: two time * and you are done. It seems trivial but it means you can write comfortably in plain text and that is a big thing because using plain text gives you access to a range of powerful versioning and collaboration tools developed for code. All of a sudden you can version and share what you do in Github and create output to a range of different formats.

But you don't need to leave LaTeX behind! If you need to type something like a mathematical formula you can simply switch to LaTeX on the fly by typing two dollar signs. So if you drop in `$$( x^2 + y^2 = 1 )$$` you get $$( x^2 + y^2 = 1 )$$.

And why stop at LaTeX? You can of course also drop in pieces of other languages like HTML and - even more interesting - R. If you want to include the square root of 3 you just type `sqrt(3)` to get 1.7320508. Or how about a plot created by doing a calculation in R? Just put in some R code and see the result. E.g.


{% highlight r %}
par(mar = c(4, 4, .1, .1))
plot(cars, pch = 19, col = 'red')  # a scatterplot
{% endhighlight %}

![A scatterplot of the cars data](/figure/source/2015-8-1-domain-specific-languages/cars-1.png) 

## Conclusions
I've tried to show that there's no such thing as a general purpose language that does it all and that you are much better of mixing and matching the right domain specific languages. It makes your code shorter and increases your productivity.
