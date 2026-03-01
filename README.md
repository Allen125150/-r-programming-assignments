# -r-programming-assignments
Allen Zagic
LIS4370
“Repository for R Programming Assignments”
data("iris")
head(iris)
class(iris)
typeof(iris)
summary(iris)
plot(iris)
S3
iris_stats <- list(
  n = nrow(iris),
  mean_sepal = mean(iris$Sepal.Length)
)

class(iris_stats) <- "iris_stats"

print.iris_stats <- function(x, ...) {
  cat("Rows:", x$n, "\n")
  cat("Mean Sepal Length:", x$mean_sepal, "\n")
}

iris_stats
S4
setClass(
  "IrisSummary",
  slots = c(
    rows = "numeric",
    mean_sepal = "numeric"
  )
)

iris_s4 <- new(
  "IrisSummary",
  rows = nrow(iris),
  mean_sepal = mean(iris$Sepal.Length)
)

iris_s4
