# -r-programming-assignments
Allen Zagic
LIS4370
“Repository for R Programming Assignments”
---
title: "My R Markdown Primer"
author: "Allen Zagic"
date: "`r Sys.Date()`"
output:
  html_document:
    toc: true
    toc_float: true
    theme: flatly
    highlight: tango
---

```{r setup, include=FALSE}
knitr::opts_chunk$set(echo = TRUE, warning = FALSE, message = FALSE)
```

---

## Introduction

R Markdown is basically a way to write a document that has your code, your
results, and your writing all in one place. Instead of running your analysis
in R and then copying everything into Word, you just write it all together and
hit knit  and it produces a clean output file automatically.

I'll be honest, I had used R before but had never really worked with R Markdown,
so there was a bit of a learning curve at first. Once I got the hang of the
structure though, it started to make a lot of sense. It feels like a more
organized way to do data work, especially when you have to actually explain
what your results mean.

---

## A Little Math

One thing R Markdown can do that regular Word documents make really annoying
is render math equations. You write them in LaTeX syntax and they show up
formatted properly in the output.

For example, a simple inline equation looks like this:
$\alpha + \beta = \gamma$

And if you want something more involved on its own line, like the least squares
formula from stats class, you can do a display equation:

$$
\hat{\boldsymbol{\beta}} = (\mathbf{X}^\top \mathbf{X})^{-1} \mathbf{X}^\top \mathbf{y}
$$

I don't claim to fully understand that second one yet, but it's good to know
R Markdown can handle it cleanly when you need it.

---

## Code Chunk 1 — Looking at the Data

For this first chunk I loaded the `mtcars` dataset which is built into R, so
there's no need to import anything. I used `dplyr` to get a quick summary of
a few variables. This part went pretty smoothly once I remembered the right
syntax.

```{r load-and-summarise}
library(dplyr)

data(mtcars)

glimpse(mtcars)

mtcars %>%
  select(mpg, hp, wt, cyl) %>%
  summary()
```

The dataset has `r nrow(mtcars)` cars total. MPG goes from `r min(mtcars$mpg)`
all the way up to `r max(mtcars$mpg)`, with an average around
`r round(mean(mtcars$mpg), 1)`. Those numbers are actually pulling straight
from the data using inline R code, which I thought was a pretty useful feature
once I figured out how it worked.

---

## Code Chunk 2 — Making a Plot

This chunk uses `ggplot2` to make a scatter plot of horsepower vs. fuel
efficiency, colored by how many cylinders each car has. I spent a little time
tweaking the colors and labels to make it look reasonable.

```{r ggplot-scatter, fig.width=7, fig.height=4.5, fig.cap="Figure 1. MPG vs. Horsepower by Number of Cylinders"}
library(ggplot2)

mtcars$cyl <- factor(mtcars$cyl, labels = c("4-cyl", "6-cyl", "8-cyl"))

ggplot(mtcars, aes(x = hp, y = mpg, colour = cyl)) +
  geom_point(size = 3, alpha = 0.8) +
  geom_smooth(method = "lm", se = FALSE, linewidth = 0.8) +
  scale_colour_manual(
    values = c("4-cyl" = "#2ecc71", "6-cyl" = "#3498db", "8-cyl" = "#e74c3c")
  ) +
  labs(
    title    = "Fuel Efficiency vs. Horsepower",
    subtitle = "mtcars dataset  |  n = 32 vehicles",
    x        = "Gross Horsepower (hp)",
    y        = "Miles per Gallon (mpg)",
    colour   = "Engine"
  ) +
  theme_minimal(base_size = 13) +
  theme(legend.position = "top")
```

The pattern is pretty clear — the more horsepower a car has, the worse the
gas mileage tends to be. The 8-cylinder cars are mostly bunched up in the
bottom right, while the 4-cylinder ones are doing much better on efficiency.
Not a surprising finding, but it's a good example of how a simple plot can
make a relationship obvious fast.

---

## Reflection

Going into this I wasn't totally sure what the point of R Markdown was versus
just writing a regular report. After actually using it, I get it more now.

The biggest thing for me was realizing that the inline R code feature means
your numbers never go out of date. If the data changes, you just re-knit and
everything updates on its own. That's something I didn't think about before
but it's actually a big deal if you're working on something long-term.

There were a couple of things that tripped me up. I kept getting errors at
first and it took me a little while to realize it was a formatting issue — you
need blank lines in the right places or things don't render the way you expect.
Also getting the chunk options right took some trial and error.

Overall though I think R Markdown is genuinely more useful than writing a plain
report. It keeps everything in one place and makes the work easier to follow,
both for other people and for yourself when you come back to it later.

---

*Compiled with R `r R.version$major`.`r R.version$minor`.*
