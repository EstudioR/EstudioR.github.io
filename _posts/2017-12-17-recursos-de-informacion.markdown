---
layout: page
title:  "Recursos de información"
categories: recursos_de_información
---


**Contenido**

* Contenido
{:toc}

# Sitios web

Algunos recursos de información en los cuales el usuario podrá encontrar múltiples
ayudas, ejemplos, tutoriales y ejercicios para desarrolar con `R` (y otros lenguajes de programación) son los siguientes:

- [Stack Overflow en inglés](https://stackoverflow.com/)
- [Stack Overflow en español](https://es.stackoverflow.com/)
- [Rpubs](https://rpubs.com/)
- [CRAN](https://cran.r-project.org/)
- [R-Studio](https://www.rstudio.com/)
- [DataCamp](https://www.datacamp.com/)
- [Github](https://github.com/)
- [edX](https://www.edx.org/es/course/subject/data-analysis-statistics)
- [R-Exercises](https://www.r-exercises.com/)
- [R-bloggers](https://www.r-bloggers.com/)

# Material bibliográfico

Además de los sitios web, también se recomienda al usuario tener en cuenta el siguiente material de apoyo:

- [*R: A Language for Data Analysis and Graphichs*](https://www.stat.auckland.ac.nz/~ihaka/downloads/R-paper.pdf)
- [*R and S*](http://vita.had.co.nz/papers/r-s.pdf)
- [*R for Beginners*](https://cran.r-project.org/doc/contrib/Paradis-rdebuts_en.pdf)
- [*R para principiantes*](https://cran.r-project.org/doc/contrib/rdebuts_es.pdf)
- [*An Introduction to R*](https://cran.r-project.org/doc/manuals/r-release/R-intro.pdf)
- [*Introduction to the R project for Statistical Computing for use at ITC*](https://cran.r-project.org/doc/contrib/Rossiter-RIntro-ITC.pdf)
- [*R for Biologists*](https://cran.r-project.org/doc/contrib/Martinez-RforBiologistv1.1.pdf)
- [*Métodos Estadísticos con R y R commander*](https://cran.r-project.org/doc/contrib/Saez-Castillo-RRCmdrv21.pdf)
- [*Statistics Using R with Biological Examples*](https://cran.r-project.org/doc/contrib/Seefeld_StatsRBio.pdf)
- [*OpenIntro Statistics*](https://www.openintro.org/download.php?file=os3_tablet)
- [*An Introduction to Statistical Learning with Applications in R*](http://www-bcf.usc.edu/~gareth/ISL/ISLR%20First%20Printing.pdf)
- [*Handbook of Biological Statistics*](http://citeseerx.ist.psu.edu/viewdoc/download?doi=10.1.1.471.3602&rep=rep1&type=pdf)
- [*Gráficos Estadísticos con R*](https://cran.r-project.org/doc/contrib/grafi3.pdf)
- [El arte de programar en R](https://cran.r-project.org/doc/contrib/Santana_El_arte_de_programar_en_R.pdf)
- [*Computational Statistics Using R and R Studio An Introduction for Scientists*](http://www.calvin.edu/~rpruim/talks/SC11/Seattle/RatSC11/Master-StatsForScience.pdf)

# Guías 

Las siguientes son guías de `R` y `R Studio` que pueden ser consultadas [aquí](https://www.rstudio.com/resources/cheatsheets/).

- [*Base R: Cheat Sheet*](https://www.rstudio.com/wp-content/uploads/2016/05/base-r.pdf)
- [*RStudio IDE Cheat Sheet*](https://www.rstudio.com/wp-content/uploads/2016/01/rstudio-IDE-cheatsheet.pdf)
- [Data Visualization with ggplot2](https://www.rstudio.com/wp-content/uploads/2015/03/ggplot2-cheatsheet.pdf)
- [R Markdown](https://www.rstudio.com/wp-content/uploads/2015/02/rmarkdown-cheatsheet.pdf)
- [Shiny](https://www.rstudio.com/wp-content/uploads/2015/02/shiny-cheatsheet.pdf)

# Ejemplos

Estos son algunos ejemplos de diversas aplicaciones que ofrece `R` y `R-Studio` dentro de la gran variedad de herramientas disponibles para el usuario. Cada código podrá ser ejecutado por el usuario, obteniendo justo la salida que se muestra debajo de cada script.

## [*Animación 2D con R*](http://www.statsblogs.com/2014/02/13/r-animating-2d-and-3d-plots/)

{% highlight r %}
library(animation)

saveGIF({
  for(i in 1:100){
    curve(sin(x), from = -5 + (i * 0.05), to = 5 + (i * 0.05), col = "red", ylab = "")
    curve(cos(x), from = -5 + (i * 0.05), to = 5 + (i * 0.05), add = TRUE, col = "blue", ylab = "")
    legend("topright", legend = c("sin(x)", "cos(x)"), fill = c("red", "blue"), bty = "n")
  }
}, interval = 0.1, ani.width = 550, ani.height = 350)
{% endhighlight %}

{:refdef: style="text-align: center;"}
![gif]({{ site.baseimg }}/images/animation1.gif)
{: refdef} 

## [*Animación 3D con R*](http://www.statsblogs.com/2014/02/13/r-animating-2d-and-3d-plots/)

{% highlight r %}
library(animation)

saveGIF({
  for(i in 1:150){
    x <- seq(-6 + (i * 0.05), 6 + (i * 0.05), length= 100)
    y <- x
    f <- function(x, y) { sin(x) + cos(y) }
    z <- outer(x, y, f)
    persp(x, y, z, theta = 45 + (i * 0.5), phi = 35, expand = 0.4, col = "lightblue")
  }
}, interval = 0.1, ani.width = 550, ani.height = 550)
{% endhighlight %}

{:refdef: style="text-align: center;"}
![gif]({{ site.baseimg }}/images/animation2.gif)
{: refdef} 

## [*Mapas con R*](https://www.r-graph-gallery.com/171-172-color-the-shapefile/)

{% highlight r %}
library(rgdal)

download.file("http://thematicmapping.org/downloads/TM_WORLD_BORDERS_SIMPL-0.3.zip" , destfile = "world_shape_file.zip")
system("unzip world_shape_file.zip")
my_spdf <- readOGR(dsn = getwd(), layer = "TM_WORLD_BORDERS_SIMPL-0.3") 
africa <- my_spdf[my_spdf@data$REGION== 2, ]
plot(africa, xlim = c(-20, 60), ylim = c(-37, 38), col = rgb(0.1, 0.9, 0.3, 0.2), bg = "#A6CAE0" )
plot(africa, xlim = c(-20, 60), ylim = c(-40, 35), col = colors()[1:100], bg = "#A6CAE0")
{% endhighlight %}

{:refdef: style="text-align: center;"}
![gif]({{ site.baseimg }}/images/Rplot.png)
{: refdef} 

 
## [*Arte con R*](https://fronkonstin.com/)

{% highlight r %}
library(dplyr)
library(ggplot2)

seq(from=-10, to=10, by = 0.05) %>%
expand.grid(x=., y=.) %>%
ggplot(aes(x=(x+pi*sin(y)), y=(y+pi*sin(x)))) +
geom_point(alpha=.1, shape=20, size=1, color="black")+
theme_void()
{% endhighlight %}

{:refdef: style="text-align: center;"}
![gif]({{ site.baseimg }}/images/Rplot02.png)
{: refdef} 


## [*Gráficos estadísticos con R*](http://www.r-graph-gallery.com/44-polynomial-curve-fitting/)

{% highlight r %}
x <- runif(300,  min=-10, max=10) 
y <- 0.1 * x^3 - 0.5 * x^2 - x + 10 + rnorm(length(x), 0, 8) 
plot(x, y, col = rgb(0.4, 0.4 ,0.8, 0.6), pch = 16, cex = 1.3) 
model <- lm(y ~ x + I(x^2) + I(x^3))
summary(model)
model$coefficients
summary(model)$adj.r.squared
myPredict <- predict(model) 
ix <- sort(x, index.return = TRUE)$ix
lines(x[ix], myPredict[ix], col = 2, lwd = 2 )  
coeff = round(model$coefficients, 2)
text(3, -70, paste("Model: ", coeff[1], " + ", coeff[2], "*x" , "+", coeff[3], "*x^2", "+", coeff[4], "*x^3", "\n\n", "P-value adjusted = ", round(summary(model)$adj.r.squared, 2)))
{% endhighlight %}

{:refdef: style="text-align: center;"}
![gif]({{ site.baseimg }}/images/Rplot03.png)
{: refdef} 

### [*Otro ejemplo de gráfico estadístico*](http://www.r-graph-gallery.com/99-scatterplot-matrix-car-package/)

{% highlight r %}
library(car)
library(RColorBrewer)

data <- mtcars
my_colors <- brewer.pal(nlevels(as.factor(data$cyl)), "Set2")
scatterplotMatrix(~mpg+disp+drat|cyl, data=data , reg.line="" , smoother="", col=my_colors , smoother.args=list(col="grey"), cex=1.5, pch=c(15,16,17), main="Scatter plot with Three Cylinder Options")
{% endhighlight %}

{:refdef: style="text-align: center;"}
![gif]({{ site.baseimg }}/images/Rplotstat.png)
{: refdef} 

[Aquí](http://rmarkdown.rstudio.com/gallery.html) hay más ejemplos y posibilades gráficas, numéricas y demás, que se pueden lograr con `R` y `R-Studio`.

