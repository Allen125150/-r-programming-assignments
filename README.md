# -r-programming-assignments
Allen Zagic
LIS4370
“Repository for R Programming Assignments”
> library(lattice)
> library(ggplot2)
> data("mtcars")
> head(mtcars)
                   mpg cyl disp  hp drat    wt  qsec vs am gear carb
Mazda RX4         21.0   6  160 110 3.90 2.620 16.46  0  1    4    4
Mazda RX4 Wag     21.0   6  160 110 3.90 2.875 17.02  0  1    4    4
Datsun 710        22.8   4  108  93 3.85 2.320 18.61  1  1    4    1
Hornet 4 Drive    21.4   6  258 110 3.08 3.215 19.44  1  0    3    1
Hornet Sportabout 18.7   8  360 175 3.15 3.440 17.02  0  0    3    2
Valiant           18.1   6  225 105 2.76 3.460 20.22  1  0    3    1
> cyl_colors <- ifelse(mtcars$cyl == 4, "green3",
+                      ifelse(mtcars$cyl == 6, "steelblue", "tomato"))
> 
> plot(mtcars$hp, mtcars$mpg,
+      col  = cyl_colors,
+      pch  = 19,
+      cex  = 1.3,
+      main = "Base: Fuel Efficiency vs. Horsepower",
+      xlab = "Horsepower (hp)",
+      ylab = "Miles Per Gallon (mpg)")
> 
> abline(lm(mpg ~ hp, data = mtcars), col = "gray30", lty = 2, lwd = 2)
> 
> legend("topright",
+        legend = c("4 cyl", "6 cyl", "8 cyl"),
+        col    = c("green3", "steelblue", "tomato"),
+        pch    = 19,
+        bty    = "n")
> par(mfrow = c(1, 3))
> 
> hist(mtcars$mpg[mtcars$cyl == 4], col = "green3",  main = "4 Cylinders", xlab = "MPG", xlim = c(10, 35), breaks = 5)
> hist(mtcars$mpg[mtcars$cyl == 6], col = "steelblue", main = "6 Cylinders", xlab = "MPG", xlim = c(10, 35), breaks = 5)
> hist(mtcars$mpg[mtcars$cyl == 8], col = "tomato",  main = "8 Cylinders", xlab = "MPG", xlim = c(10, 35), breaks = 5)
> 
> par(mfrow = c(1, 1))
> xyplot(mpg ~ wt | factor(cyl),
+        data   = mtcars,
+        main   = "Lattice: MPG vs. Weight by Cylinders",
+        xlab   = "Weight (1000 lbs)",
+        ylab   = "Miles Per Gallon (mpg)",
+        pch    = 19,
+        col    = "steelblue",
+        type   = c("p", "r"),
+        layout = c(3, 1))
> bwplot(mpg ~ factor(cyl) | factor(am, labels = c("Automatic", "Manual")),
+        data = mtcars,
+        main = "Lattice: MPG by Cylinders and Transmission Type",
+        xlab = "Number of Cylinders",
+        ylab = "Miles Per Gallon (mpg)")
> ggplot(mtcars, aes(x = hp, y = mpg, color = factor(cyl))) +
+     geom_point(size = 3) +
+     geom_smooth(method = "lm", se = FALSE) +
+     labs(title = "ggplot2: Fuel Efficiency vs. Horsepower by Cylinders",
+          x     = "Horsepower (hp)",
+          y     = "Miles Per Gallon (mpg)",
+          color = "Cylinders") +
+     theme_minimal()
`geom_smooth()` using formula = 'y ~ x'
> ggplot(mtcars, aes(x = mpg, fill = factor(cyl))) +
+     geom_histogram(binwidth = 2, color = "white") +
+     facet_wrap(~ factor(cyl), labeller = label_both) +
+     labs(title = "ggplot2: MPG Distribution by Cylinder Count",
+          x     = "Miles Per Gallon (mpg)",
+          y     = "Count",
+          fill  = "Cylinders") +
+     theme_minimal() +
+     theme(legend.position = "none")
