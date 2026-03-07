# -r-programming-assignments
Allen Zagic
LIS4370
“Repository for R Programming Assignments”
> library(plyr)
> 
> students <- read.csv(file.choose(), header = TRUE)
> 
> students_gendered_mean <- ddply(students, "Sex", summarise,
+                                 Grade_Average = mean(Grade, na.rm = TRUE))
> 
> write.table(students_gendered_mean,
+             "Students_Gendered_Mean.txt",
+             row.names = FALSE)
> 
> i_students <- subset(students, grepl("i", Name, ignore.case = TRUE))
> 
> write.csv(i_students,
+           "i_students.csv",
+           row.names = FALSE)
+ 
