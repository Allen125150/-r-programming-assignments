# -r-programming-assignments
Allen Zagic
LIS4370
“Repository for R Programming Assignments”
A <- matrix(c(2, 0, 1, 3), ncol = 2)
B <- matrix(c(5, 2, 4, -1), ncol = 2)

A + B
A - B

diag(c(4, 1, 2, 3))

M <- diag(3, 5)
M[1, ] <- c(3, 1, 1, 1, 1)
M[-1, 1] <- 2
M
