# -r-programming-assignments
Allen Zagic
LIS4370
“Repository for R Programming Assignments”
A <- matrix(1:100, nrow = 10)
> B <- matrix(1:1000, nrow = 10)
> det_A <- det(A)
> det_A
[1] 0
> solve(A)
Error in solve.default(A) : 
  Lapack routine dgesv: system is exactly singular: U[8,8] = 0
> 
