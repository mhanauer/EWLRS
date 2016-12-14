# EWLRS
data = read.csv("EWLRS.Data-3.csv", header = TRUE)
data = scale(data)
head(data)
# data.1 is creating a mean of the variables
data.1 = apply(data, 1, mean)
head(data.1)
# data.2 orders data.1 by largest value
data.2 = data.1[order(data.1, decreasing = TRUE)]
head(data.2)
# data.3 demonstrates the top 30 most needy indiviudals
data.3 = data.2[1:30]; data.3
# data.4 demonstrates taking everyone over zero
data.4 = data.2[data.2 > 0]; data.4
write(data.2, "EWLRS.Data-5.csv")
