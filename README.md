# -r-programming-assignments
Allen Zagic
LIS4370
“Repository for R Programming Assignments”
Frequency <- c(0.6, 0.3, 0.4, 0.4, 0.2, 0.6, 0.3, 0.4, 0.9, 0.2)

BP <- c(103, 87, 32, 42, 59, 109, 78, 205, 135, 176)

First <- c(1, 1, 1, 1, 0, 0, 0, 0, NA, 1)

Second <- c(0, 0, 1, 1, 0, 0, 1, 1, 1, 1)

FinalDecision <- c(0, 1, 0, 1, 0, 1, 0, 1, 1, 1)
boxplot(BP,
        main = "Boxplot of Patient Blood Pressure",
        ylab = "Blood Pressure",
        col = "lightgray")
hist(BP,
     main = "Histogram of Patient Blood Pressure",
     xlab = "Blood Pressure",
     col = "lightblue",
     breaks = 5)
