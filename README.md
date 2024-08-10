NASA Asteroid Prediction
By: Aditya Kumar Mishra
Overview
This project aims to predict asteroid impacts using data from NASA. The analysis is performed using R, and various statistical and machine learning techniques are applied to understand and predict asteroid behavior.

Files
nasa.csv: The dataset containing information about asteroids.
nasa_asteroid_prediction.R: The R script containing the code for data analysis and prediction.
Requirements
R (version 4.0.0 or higher)
R libraries: ggplot2, rpart, rpart.plot
Installation
Install R from CRAN.
Install the required libraries by running the following commands in R:
R

install.packages("ggplot2")
install.packages("rpart")
install.packages("rpart.plot")
AI-generated code. Review and use carefully. More info on FAQ.
Usage
Load the dataset:
R

astr <- read.csv("D:/R FOLDER/nasa.csv")
AI-generated code. Review and use carefully. More info on FAQ.
Check the data:
R

head(astr)
str(astr)
tail(astr)
AI-generated code. Review and use carefully. More info on FAQ.
Data correction and visualization:
R

sum(is.na(astr))
pairs(astr[,1:4], col = astr$Miles.per.hour, main = "Asteroid Speed Plotting")
AI-generated code. Review and use carefully. More info on FAQ.
Data sampling:
R

set.seed(123)
sample_indices <- sample(1:nrow(astr), 0.7 * nrow(astr))
train_data <- astr[sample_indices,]
test_data <- astr[-sample_indices,]
AI-generated code. Review and use carefully. More info on FAQ.
Create a histogram:
R

hist(astr$Epoch.Date.Close.Approach, col = rainbow(12), breaks = 12, main = "Colorful Histogram of Epoch Date Close Approach", xlab = "Epoch Date Close Approach")
AI-generated code. Review and use carefully. More info on FAQ.
Linear model and prediction:
R

model <- lm(Absolute.Magnitude ~ Mean.Motion, data = astr)
plot(model)
summary(model)

new_data <- data.frame(Mean.Motion = c(0.5, 1, 1.5))
new_pred <- predict(model, new_data)
cat("Predictions for new data:", new_pred, "\n")
AI-generated code. Review and use carefully. More info on FAQ.
Decision tree model:
R

library(rpart)
model <- rpart(Neo.Reference.ID ~ Absolute.Magnitude + Relative.Velocity.km.per.hr + Orbital.Period + Miss.Dist..miles., data = train_data)
library(rpart.plot)
rpart.plot(model, main = "Decision Tree")
AI-generated code. Review and use carefully. More info on FAQ.
Output
The output includes various plots and predictions based on the models created. The decision tree model visualizes the relationship between different asteroid characteristics and their potential impact.
