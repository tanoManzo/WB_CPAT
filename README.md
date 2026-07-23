# Household Air Pollution and Energy Use

This project studies how household air pollution (HAP) changes with energy
consumption, with particular attention to coal and biomass fuels.

## Data

The current analysis uses the IHME Global Burden of Disease 2023 household
air-pollution estimates for 1990–2023. The annual files distinguish:

- Coal and charcoal (`rei_id = 394`)
- Wood (`rei_id = 395`)
- Agricultural residue (`rei_id = 396`)
- Dung (`rei_id = 397`)
- All solid fuels (`rei_id = 87`)

Wood, agricultural residue, and dung are treated as separate biomass
categories. The annual files are stacked into a longitudinal panel; values are
not averaged across years.

The source data are not committed to this repository. Place the downloaded CSV
files in:

```text
data/IHME_GBD_2023_AIR_POLLUTION_1990_2023_HAP/
data/energy/EnergyConsumption_1970_to_2019 raw v2.csv
data/energy/biomass/
```

## Analysis

Run the notebooks in this order:

1. [`analysis/hap_energy_merge.ipynb`](analysis/hap_energy_merge.ipynb)
   combines IHME HAP with residential coal and biomass consumption from the
   energy dataset. It retains the detailed UN biomass series as supplementary
   variables, matches country identifiers, and writes
   `data/processed/hap_energy_biomass_panel.csv`.
2. [`analysis/hap_coal_biomass_basic.ipynb`](analysis/hap_coal_biomass_basic.ipynb)
   provides a short exploratory analysis and loads the processed panel.
3. [`analysis/hap_energy_regression.ipynb`](analysis/hap_energy_regression.ipynb)
   converts coal and biomass consumption to residential-energy shares,
   estimates a first-difference model with country-clustered standard errors,
   and provides a baseline projection function.

- Loads and combines the 34 annual files
- Selects the proportion measure for both sexes and all ages
- Checks the resulting location-year-fuel panel
- Compares global exposure in 1990 and 2023
- Plots global trends for coal and the three biomass categories
- Reports coverage after linking HAP to coal and biomass consumption

The preliminary global estimates show the largest decline for wood exposure,
from 43.72% in 1990 to 20.46% in 2023. Coal and charcoal declined from 9.66% to
5.17%. These results are descriptive and should not be interpreted as causal
effects of energy consumption.

## Setup

The project uses Python 3.12 and
[`uv`](https://docs.astral.sh/uv/) for dependency management.

```bash
uv sync
uv run jupyter lab
```

Open `analysis/hap_energy_merge.ipynb` first, followed by
`analysis/hap_coal_biomass_basic.ipynb` and
`analysis/hap_energy_regression.ipynb`.

## Regression

The regression explains annual changes in overall solid-fuel HAP using annual
changes in coal and biomass shares of residential energy. It also controls for
changes in total residential energy per capita. Coal and biomass coefficients
are expressed as changes in HAP percentage points per one-percentage-point
change in the corresponding energy share.

The projection function anchors each country to its latest observed HAP and
applies projected energy-share changes plus the estimated historical trend.
The included 2010–2019 backtest provides a basic validation check.
Robustness checks also examine five-year changes, coal-using countries, and an
approximate coal-plus-charcoal measure assembled from the UN household series.

These estimates support baseline scenario analysis but should not be
interpreted as causal effects without a stronger identification strategy,
additional controls, and explicit projection uncertainty.
