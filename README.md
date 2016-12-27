data = read.csv("EWLRS.Data-4.csv", header = TRUE)
head(data)
# data.1 scales the variables
data.1 = scale(data); head(data.1)
# data.2 now drops the student.id variable, because it was scaled and doesn't make sense
data.1 = as.data.frame(data.1)
data.2 = data.1[c(-1)]; head(data.2) 
# data.3 is creating a mean of the variables
data.3 = apply(data.2, 1, mean); head(data.3)
# data.4 is adding back student.id before ordering
data.3 = as.data.frame(data.3)
data.4 = cbind(data$Student.ID, data.3); head(data.4)
# data.5 orders data.1 by largest value for EWLRS.Risk.Factor (i.e. data.3)
data.5 = data.4[order(-data.3),]; head(data.5)
# data.5 demonstrates the top 30 most needy indiviudals
# data.6 displays the first 30 students with both id and risk factor
data.6 = data.5[1:30,]; data.6
# data.7 demonstrates taking everyone over zero, but still not working
data.7 = data.5[,2] > 0; data.7
data.5[,2]
write.csv(data.5, "EWLRS.Data-6.csv")
