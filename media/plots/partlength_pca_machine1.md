
library(qcc)

# Filter data for Machine 1, Temperature 338K, Pressure 200kPa
filtered_data_cap <- subset(X026..1., Machine == 1 & Temperature == 338 & Pressure == 200)

# Define LSL and USL
LSL <- 45
USL <- 55

# Create a qcc object (e.g., xbar chart) first, assuming subgroup size n=5
qcc_object_pl <- qcc(filtered_data_cap$PartLength, type = "xbar", sizes = 5, plot = FALSE)

# Perform Process Capability Analysis for PartLength
pca_result_pl <- process.capability(qcc_object_pl,
                                    spec.limits = c(LSL, USL),
                                    target = mean(filtered_data_cap$PartLength, na.rm = TRUE))

# Print summary of results
print(summary(pca_result_pl))

# Plot the capability analysis (will render in R output, not as HTML widget easily)
plot(pca_result_pl)

