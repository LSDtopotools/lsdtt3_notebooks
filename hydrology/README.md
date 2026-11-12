# Hydrology notebooks

Two notebooks run the two hydrological models in `lsdtt-distributed-hydrology` on the same catchment: the **Ettrick Water above Brockhoperig** in the Southern Uplands of Scotland (NRFA gauging station 21017, 37.5 km²), with a 30 m Copernicus DEM, weather from Open-Meteo and flows from the National River Flow Archive. Both install everything they need in Colab.

| Notebook | Model | What it does |
|---|---|---|
| [`s_hype_simulation.ipynb`](s_hype_simulation.ipynb) | S-HYPE (`column_model: hype`) | Three years of daily flows; a quick calibration with SPOTPY; a second soil class along the channels |
| [`topmodel_storm.ipynb`](topmodel_storm.ipynb) | TOPMODEL (`column_model: topmodel`) | One storm (October 2021) at hourly steps; maps of the catchment wetting up |

## Two ways of building a catchment model

**S-HYPE** (Lindström et al., 2010; Strömqvist et al., 2012) is **semi-distributed**. The catchment is divided into sub-basins, and each sub-basin into classes (land use × soil) that are known only by their **area fractions**, not their locations. Each class runs a soil column with snow, evapotranspiration and up to three soil layers; the sub-basins are routed through their rivers. It runs at **daily** steps and is built for **seasons and years**: snow, summer drying, low flows, many gauges at once. Its classes do not exchange water, so it cannot represent valley floors kept wet by water draining into them from the hillslopes above.

**TOPMODEL** (Beven and Kirkby, 1979) is **distributed**: it works on every pixel of the DEM. Its central idea is that water drains downslope underground, so the ground saturates first where much upslope area drains through a gentle slope, measured by the topographic wetness index ln(a / tan β). Rain on saturated ground runs straight off, and the saturated area grows and shrinks with the wetness of the catchment. It runs at **any time step** (hourly in the notebook) and is built for **storms**, and for **where** the catchment saturates. It has no snow and, in the form used here, no separate groundwater or seasonal evapotranspiration model, so it is not suited to long runs through dry summers and cold winters.

In short: S-HYPE says **how much** water leaves the catchment over months and years; TOPMODEL says **where** the water comes from in a storm.

## Computational expense

Both are cheap at this size. Measured on one laptop (8 cores) for the Ettrick catchment, 39 km² at 30 m:

| Run | Units of computation | Wall time |
|---|---|---|
| S-HYPE, 3 years, daily (1096 steps) | 1 sub-basin × 1 class | 0.2–0.4 s |
| S-HYPE calibration in the notebook (SPOTPY, about 410 runs of 2 years) | as above | about 80 s |
| TOPMODEL, index mode, 6-day storm, hourly (144 steps) | about 42,000 pixels | 0.2–0.4 s |
| TOPMODEL, dynamic saturated zone, the same storm | about 42,000 pixels | about 0.9 s |

Each run includes reading the DEM, filling it and routing flow over it. Colab's free machines are slower than this laptop, so expect two or three times longer. Laptop timings also vary with how hot the machine is.

How the cost grows is what differs:

* **S-HYPE** costs one soil-column update per **sub-basin × class × day**, plus the DEM processing at the start. A large catchment with many classes still has only hundreds or thousands of units, so years of daily simulation stay cheap, and a calibration of thousands of runs is practical.
* **TOPMODEL** costs one update per **pixel × time step**. Finer DEMs and longer runs multiply it: a 10 m DEM has nine times the pixels of a 30 m one, and a year of hourly steps is 60 times this storm. The dynamic saturated zone, which moves water from pixel to pixel down the flow network, costs a few times more than the classic index mode, and may need sub-steps for stability. Calibrating TOPMODEL over long periods at fine resolution is therefore much more expensive than calibrating S-HYPE.

## References

* Beven, K. J. and Kirkby, M. J. (1979). A physically based, variable contributing area model of basin hydrology. *Hydrological Sciences Bulletin*, 24(1), 43–69. https://doi.org/10.1080/02626667909491834
* Lindström, G., Pers, C., Rosberg, J., Strömqvist, J. and Arheimer, B. (2010). Development and testing of the HYPE (Hydrological Predictions for the Environment) water quality model for different spatial scales. *Hydrology Research*, 41(3–4), 295–319. https://doi.org/10.2166/nh.2010.007
* Strömqvist, J., Arheimer, B., Dahné, J., Donnelly, C. and Lindström, G. (2012). Water and nutrient predictions in ungauged basins: set-up and evaluation of a model at the national scale. *Hydrological Sciences Journal*, 57(2), 229–247. https://doi.org/10.1080/02626667.2011.637497
* lsdtt3 documentation of both models: https://lsdtopotools.github.io/lsdtt3/design_and_algorithms/hydrological_modelling.html
