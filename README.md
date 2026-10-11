# Spatiotemporal Patterns of Crime in Chicago (2012–2016)

A statistical analysis of about 1.4 million reported crimes in Chicago, written in **R**. The project looks at **where** crime happens, **when** it happens, and whether weekly crime counts can be **forecast** with a time-series model.

This was a course project for *Computational Statistics* (Prof. Zaussinger) at **Hochschule Mittweida – University of Applied Sciences**.

<p align="center">
  <a href="poster/poster.pdf">
    <img src="poster/poster.png" alt="Project poster: Spatiotemporal Patterns of Crime in Chicago" width="900">
  </a>
  <br>
  <em>Project poster (click for the PDF)</em>
</p>

---

## Questions

1. **Time:** How does crime change across the days of the week and the hours of the day?
2. **Place:** Do the high-crime areas stay the same from year to year?
3. **Crime type:** Do different crime types cluster in different parts of the city?
4. **Forecasting:** Can an ARIMA model predict weekly crime counts for a year it has not seen?

## Key results

| Question | Method | Result |
|---|---|---|
| Hotspot stability | Pearson correlation of counts per community area, 2012 vs. 2016 | **R = 0.98**: the same areas stay at the top |
| Crime type vs. location | Chi-squared test of independence (top 4 crime types, 2016) | p < 2.2e-16: crime types are not spread evenly across the city |
| Day of the week | One-way ANOVA on daily counts, plus Tukey post-hoc | **F = 6.51, p < 0.001**: Friday is the peak day |
| Time of day | Welch t-test, midnight–8 AM vs. rest of day | Clearly fewer incidents at night |
| Forecasting | ARIMA trained on 2012–2015 weekly counts, tested on 2016 | **MAPE = 5.22%** |

## Data

- **Crimes in Chicago**, Kaggle dataset by *Currie32*: [kaggle.com/datasets/currie32/crimes-in-chicago](https://www.kaggle.com/datasets/currie32/crimes-in-chicago). The project uses the file `Chicago_Crimes_2012_to_2017.csv`, an export from the City of Chicago Data Portal.
- **Chicago Community Areas GeoJSON**, Kaggle dataset by *Doyouevendata*, used for the maps.

Cleaning steps:
- dropped rows without coordinates
- dropped 2017, since that year is incomplete
- parsed timestamps into year, month, weekday and hour

After cleaning, **1,419,601** incidents remain.

## Methods

- **Exploration:** heatmap of crimes by weekday and hour, plus choropleth maps of community areas with `sf` and `ggplot2`
- **Distribution check:** Q-Q plot, Shapiro-Wilk test, skewness and kurtosis of daily counts
- **Time patterns:** one-way ANOVA with Tukey HSD, and a Welch two-sample t-test
- **Spatial patterns:** Pearson correlation between years, and a chi-squared test for crime type × community area
- **Forecasting:** `auto.arima` on weekly counts (frequency 52), evaluated with MAPE on the held-out 2016 data

## Repository structure

```
├── chicago-crime-data-project-in-r.ipynb   # full analysis (R kernel)
├── poster/
│   ├── poster.pdf                          # project poster
│   └── poster.png                          # preview image used in this README
└── README.md
```

## Tools

R · tidyverse · lubridate · sf · ggplot2 · ggpubr · moments · forecast · Jupyter

## Author

**Ali Issa**, Applied Mathematics, Hochschule Mittweida
GitHub: [@aliissa824](https://github.com/aliissa824) · LinkedIn: [aliissa824](https://www.linkedin.com/in/aliissa824)
