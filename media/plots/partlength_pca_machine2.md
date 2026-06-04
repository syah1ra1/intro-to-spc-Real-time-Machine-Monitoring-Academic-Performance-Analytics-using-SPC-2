
library(qcc)
filtered_data_cap_m2 <- subset(X026..1., Machine == 2 & Temperature == 338 & Pressure == 200)
LSL <- 45; USL <- 55
qcc_object_pl_m2 <- qcc(filtered_data_cap_m2$PartLength, type = "xbar", sizes = 5, plot = FALSE)
pca_result_pl_m2 <- process.capability(qcc_object_pl_m2, spec.limits = c(LSL, USL), target = mean(filtered_data_cap_m2$PartLength, na.rm = TRUE))
print(summary(pca_result_pl_m2))
plot(pca_result_pl_m2)
