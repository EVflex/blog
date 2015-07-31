---
title: "Untitled"
author: "Auke Hoekstra"
date: "29 juli 2015"
output: ioslides_presentation
<!-- output: ioslides_presentation -->
---

## R Markdown

This is an R Markdown presentation. Markdown is a simple formatting syntax for authoring HTML, PDF, and MS Word documents. For more details on using R Markdown see <http://rmarkdown.rstudio.com>.

When you click the **Knit** button a document will be generated that includes both content as well as the output of any embedded R code chunks within the document.

## Slide with Bullets

- Bullet 1
- Bullet 2
- Bullet 3

## Slide with R Code and Output


```r
summary(cars)
```

```
##      speed           dist       
##  Min.   : 4.0   Min.   :  2.00  
##  1st Qu.:12.0   1st Qu.: 26.00  
##  Median :15.0   Median : 36.00  
##  Mean   :15.4   Mean   : 42.98  
##  3rd Qu.:19.0   3rd Qu.: 56.00  
##  Max.   :25.0   Max.   :120.00
```

## Slide with Plot

![plot of chunk unnamed-chunk-2](/figure/source/example-presentation/unnamed-chunk-2-1.png) 


![](../pics/knit-logo.png)

**I feel we have all the tools to create a better scientific worklow. One that facilitates free information sharing, reproducible science and real collaboration. This first post gives the outline.***

![](../pics/workflow.svg)

## One integral reproducible source
It is hard be integral and reproducible - to yourself and to others - if what you do is scattered in many pieces. Hence the popularity from documents containing Text and code at the same time. 

Mathematicians like to use Latex so they can include their formula's in the text. Many even like to mix include live calculations and the resulting graphs. For example in the "notebooks" of iPython, mathematica and RStudio. In programming no one less than Donald Knuth spearheaded the "literate programming" movement.

##![](../pics/donald-knuth.jpg)

I will show how R Markdown is ideally suited to contain many different types of source material as outlined in the picture. It is also nice that all mentioned tools are free and open source. Incidently, markdown is also much easier to work with than the (admittedly more powerful) Latex.

# Real collaboration

##
Collaboration is a really popular word these days but ask yourself this: can some brilliant kid in another country freely read what you have written and easily propose specific changes in the document that you can integrate in the document with mininum fuss?

##  
![](../pics/linus-torvalds.jpg)

I would argue that this was exactly what happened during the development of Linux. Imagine keeping track of the many contributions of thousands of contributors through endless iterations. And no sloppy work allowed: one typo can bring the whole program crashing down. I think this process should be an inspiration for those calling themselves scientists. The big publishers will not like because it undermines their earnings but tools like Git and sites like Github make it really easy to implement...

# Write once - publish anywhere
With the process we just described you can quickly merge the contributions of others, make some last improvements to your text, calculations and graphs, rerun" your document and then... with just a few commands... your HTML document, PDF, Word document or web page is out the door.