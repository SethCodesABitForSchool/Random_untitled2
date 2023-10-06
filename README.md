# Random_untitled2
data <- read.csv('~/Downloads/econ1.csv')
data_subset <- subset(data, )
colnames(data)
row.names(data)
subset_data <- data[, c("Date", "All_items", "Excluding_food_and_energy")]

plot(data$VALUE, main = "GDP", xlab = "date", ylab = "values", col= "blue", type = "l")

head(Products.and.product.groups)

# Assuming 'data' is your data frame
subset_data <- data[data$Products.and.product.groups %in% c("All-items", "All-items excluding food and energy"), c("REF_DATE", "GEO", "VALUE")]

# Check the first few rows of the subset data
head(subset_data)

# Extract "REF_DATE" and "VALUE"
extracted_data <- subset_data[, c("REF_DATE", "VALUE")]


# Check the first few rows of the extracted data
head(extracted_data)

extracted_data$REF_DATE <- as.Date(extracted_data$REF_DATE, format = "%Y-%m")



# Convert 'REF_DATE' to Date type
extracted_data$REF_DATE <- as.Date(extracted_data$REF_DATE)

# Create time series object
monthly_ts <- ts(extracted_data$VALUE, start = start(extracted_data$REF_DATE), frequency = 12)

# Calculate Year-on-Year rates
yoy_monthly <- 100 * (monthly_ts / lag(monthly_ts, 12) - 1)

# Plot the Year-on-Year rates at monthly frequency
plot(extracted_data$REF_DATE, yoy_monthly, type = "l", col = "blue", lwd = 2, main = "Monthly CPI Inflation (YoY)", ylab = "Inflation Rate")


# Convert 'REF_DATE' to Date type
extracted_data$REF_DATE <- as.Date(extracted_data$REF_DATE, format = "%Y-%m")

# Check for missing values in 'REF_DATE' or 'VALUE'
missing_values <- is.na(extracted_data$REF_DATE) | is.na(extracted_data$VALUE)

# Remove rows with missing values
extracted_data <- extracted_data[!missing_values, ]

# Create time series object
monthly_ts <- ts(extracted_data$VALUE, start = start(extracted_data$REF_DATE), frequency = 12)

# Calculate Year-on-Year rates
yoy_monthly <- 100 * (monthly_ts / lag(monthly_ts, 12) - 1)

# Plot the Year-on-Year rates at monthly frequency
plot(extracted_data$REF_DATE, yoy_monthly, type = "l", col = "blue", lwd = 2, main = "Monthly CPI Inflation (YoY)", ylab = "Inflation Rate")


# Check the dimensions of extracted_data and yoy_monthly
cat("Dimensions of extracted_data:", dim(extracted_data), "\n")
cat("Length of yoy_monthly:", length(yoy_monthly), "\n")


head(extracted_data)
head(yoy_monthly)


# Remove rows with missing values in 'REF_DATE'
extracted_data <- na.omit(extracted_data)
View(missing_values)

# Convert 'REF_DATE' to Date type
extracted_data$REF_DATE <- as.Date(extracted_data$REF_DATE, format = "%Y-%m")

install.packages("zoo")
library(zoo)

# Create time series object
monthly_ts <- ts(extracted_data$VALUE, start = start(extracted_data$REF_DATE), frequency = 12)

# Calculate Year-on-Year rates
yoy_monthly <- 100 * (monthly_ts / lag(monthly_ts, 12) - 1)

# Plot the Year-on-Year rates at monthly frequency
plot(unique_data$REF_DATE, yoy_monthly, type = "l", col = "blue", lwd = 2, main = "Monthly CPI Inflation (YoY)", ylab = "Inflation Rate")

# Remove rows with missing values
extracted_data <- na.omit(monthly_ts)

# Example: Impute missing values with the mean of the column
extracted_data$VALUE[is.na(extracted_data$VALUE)] <- mean(extracted_data$VALUE, na.rm = TRUE)

library(zoo)
# Create time series objects
monthly_ts <- zoo(unique_data$VALUE, order.by = extracted_data$REF_DATE)



# Remove duplicate entries
unique_data <- extracted_data[!duplicated(extracted_data$REF_DATE), ]

# Convert 'REF_DATE' to Date type
unique_data$REF_DATE <- as.Date(unique_data$REF_DATE, format = "%Y-%m")

# Create zoo object
monthly_ts <- zoo(unique_data$VALUE, order.by = unique_data$REF_DATE)





