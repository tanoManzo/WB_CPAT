# Household Air Pollution and Residential Energy Use

## Short findings report

The goal of this analysis is to model changes in household air pollution (HAP)
under a baseline energy scenario. The main interest is the effect of changes in
residential coal and biomass consumption.

The analysis combines IHME household air pollution data with residential energy
consumption data for 139 countries from 1990 to 2019. Coal and biomass are
measured as shares of total residential energy. This is more suitable than
using total consumption because HAP measures the share of the population
exposed to polluting fuels.

The model uses annual changes. The HAP variable is measured in percentage
points. The coal and biomass variables are also measured in percentage points
of residential energy. Standard errors are grouped by country.

The main model uses 3,963 annual changes from 139 countries.

| Variable | Coefficient | Standard error | P-value | 95% confidence interval |
|---|---:|---:|---:|---:|
| Coal share | 0.0043 | 0.0089 | 0.632 | -0.0132 to 0.0217 |
| Biomass share | 0.0346 | 0.0084 | <0.001 | 0.0182 to 0.0510 |
| Total energy per person | -0.1602 | 0.1204 | 0.184 | -0.3962 to 0.0759 |
| Annual background trend | -0.5207 | 0.0431 | <0.001 | -0.6052 to -0.4363 |

The biomass result means that a one percentage point increase in the biomass
share is linked with a 0.0346 percentage point increase in HAP. In the same
way, a 10 percentage point decrease in the biomass share is linked with a 0.346
percentage point decrease in HAP.

The sensitivity checks give the following results:

| Check | Coefficient | Standard error | P-value | 95% confidence interval | Observations |
|---|---:|---:|---:|---:|---:|
| Five-year coal | -0.0118 | 0.0370 | 0.749 | -0.0843 to 0.0606 | 3,407 |
| Coal-use countries | -0.0003 | 0.0075 | 0.963 | -0.0151 to 0.0144 | 1,345 |
| Coal plus charcoal | 0.0019 | 0.0066 | 0.772 | -0.0110 to 0.0148 | 2,229 |
| Five-year biomass | 0.1238 | 0.0281 | <0.001 | 0.0686 to 0.1790 | 3,407 |

None of the coal tests produced a reliable coefficient. Coal use is zero in
many countries and changes very little in many others. This makes its effect
difficult to estimate with the available data. The biomass result remains
positive and significant in the five-year model.

The model also finds an average background decline in HAP of about 0.52
percentage points per year. This trend may reflect income growth,
electrification, urbanization, cleaner stoves, and other changes that are not
fully captured by the energy variables.

The model can be used for baseline projections. Each projection starts from the
latest observed HAP level for a country. It then applies projected changes in
coal and biomass shares, total residential energy per person, and the estimated
background trend. A historical test for 2011 to 2019 gives a mean absolute
error of about 1.98 percentage points.

The biomass coefficient can be used in the baseline model with a confidence
range. The coal coefficient should be used with caution because the data do not
give a precise estimate. These results describe historical relationships. They
do not prove that changes in energy use directly cause changes in HAP.
