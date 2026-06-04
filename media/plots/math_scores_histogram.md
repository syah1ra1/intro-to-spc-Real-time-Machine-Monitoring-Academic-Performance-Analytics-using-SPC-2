
library(ggplot2)
library(plotly)
library(htmlwidgets)

# Create the histogram
p <- ggplot(bigclass, aes(x = Math)) +
  geom_histogram(binwidth = 50, fill = "#0072B2", color = "white") +
  labs(
    title = "Distribution of Math Scores",
    x = "Math Score",
    y = "Frequency"
  ) +
  theme_minimal() +
  theme(
    plot.background = element_rect(fill = "white", color = NA),
    panel.background = element_rect(fill = "white", color = NA),
    axis.title.x = element_text(size = 18),
    axis.title.y = element_text(size = 18),
    axis.text.x = element_text(size = 14),
    axis.text.y = element_text(size = 14)
  )

# Convert to plotly object
p_plotly <- ggplotly(p)

# Save as HTML widget
output_html_path <- "media/plots/math_scores_histogram.html"
saveWidget(p_plotly, file = output_html_path, selfcontained = TRUE)

