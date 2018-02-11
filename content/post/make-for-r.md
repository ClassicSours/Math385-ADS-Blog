---
title: Make File in R
author: Aaron Shaffer
date: '2018-02-10'
slug: make-for-r
categories:
  - R
tags:
  - make
  - plot
  - R Markdown
header:
  caption: ''
  image: ''
---

This is the tutorial for my makefile for r, My makefile is as follows:

```{r}
all: gapminder

gapminder:
	Rscript -e "knitr::knit('gapminder.Rmd');/
  rmarkdown::render('gapminder.Rmd','html_document')"

clean:
	rm -rf *.md
	rm -rf *.html
```
What this makefile does is call the knit package on my `gapminder.Rmd` file and then call the `rmarkdown::render()` function on my file to knit the file and render it to `.html`

You can find the link to that html [here!](./assignment1/gapminder.html)


In order to format the page to look nice I lie a bit in how my code is represented to the viewer.

By default all plots are left aligned but I wanted my plots to all be centered but wrapping a `<center>` tag around an `r` section also centers the code in that section so all of the plots are actually called like.

```{r}
    ```{r, eval = FALSE}
    ggplotly(gapminder.gg)
    ```
    ```{r}
    <center>
    ```{r, echo = FALSE}
    ggplotly(gapminder.gg + xlab(""))  %>% layout(xaxis = list(title = "Year"))
    ```
    </center>
```

Sometimes I even added extra flourish like above to coax the graph into looking how I wanted it to appear.
