# lsdtt3_notebooks

![Drainage divides of third- and fourth-order basins over shaded relief, drawn with lsdviztools3 from lsdtt3 output](images/readme_banner.png)

Jupyter notebooks for topographic analysis on [Google Colab](https://colab.research.google.com/) with **lsdtt3** (LSDTopoTools3) and **lsdviztools3**. Each one is a worked example on a real landscape that you can open in Colab and run from top to bottom, then change for your own area.

**Both packages are still in development, so these notebooks should be considered experimental.**

## The software

The notebooks use two open-source packages:

| | What it is | Code | Documentation | DOI |
|---|---|---|---|---|
| **lsdtt3** (LSDTopoTools3) | C++ command-line tools and a Python package for topographic analysis: DEM preprocessing, flow routing, channel and basin extraction, chi and channel steepness, surface metrics, hydrological and landscape evolution modelling | [github.com/LSDtopotools/lsdtt3](https://github.com/LSDtopotools/lsdtt3) | [lsdtopotools.github.io/lsdtt3](https://lsdtopotools.github.io/lsdtt3/) | [![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.24110423.svg)](https://doi.org/10.5281/zenodo.24110423) |
| **lsdviztools3** | Python package for maps and charts of lsdtt3 output, drawn with PyGMT and matplotlib | [github.com/LSDtopotools/lsdviztools3](https://github.com/LSDtopotools/lsdviztools3) | [lsdtopotools.github.io/lsdviztools3](https://lsdtopotools.github.io/lsdviztools3/) | [![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.24113499.svg)](https://doi.org/10.5281/zenodo.24113499) |

Every lsdtt3 command-line program also documents itself: `<program> -h` lists every parameter it accepts, and `<program> -h <parameter_name>` explains one.

If you use them in your work, please cite them. These DOIs always point to the latest version:

> Mudd, S. M., Vervoordeldonk, R., Gailleton, B., Hawksworth, M. E., Clubb, F. J., Grieve, S. W. D., Milodowski, D. T., Valters, D. and Hurst, M. D. LSDTopoTools3 (lsdtt3): topographic analysis for geomorphology. Zenodo. https://doi.org/10.5281/zenodo.24110423

> Mudd, S. M. and Vervoordeldonk, R. lsdviztools3: visualisation tools for LSDTopoTools3. Zenodo. https://doi.org/10.5281/zenodo.24113499

Most notebooks also download data (DEMs, lidar, geological maps, river lines, weather and river flows), and each source has its own licence and citation: cite those too. The notebooks name their sources, and the newer ones list them at the end.

## Contents

- `surface_metrics/`: a hillshade and topographic gradient
- `channel_extraction/`: extracting channel networks and basins, including from your own area and outlets
- `chi_analysis/`: chi analysis: concavity from the disorder method, channel steepness (k<sub>sn</sub>) and knickpoints
- `landscape_transience/`: common analyses for checking whether a landscape is transient
- `lithology/`: comparing channel steepness (k<sub>sn</sub>) and hillslope metrics across the units of a geological map
- `channel_cross_sections/`: tracing a mapped river (OS Open Rivers) and drawing swath cross sections of its valley from lidar
- `floodplains_and_valleys/`: mapping floodplains and measuring valley widths
- `dealing_with_field_point_data/`: tying field measurements (widths, grain sizes) to the channel network: snapping GPS points to channels and adding drainage area, gradient and chi
- `hydrology/`: hydrological modelling of a gauged catchment with S-HYPE (daily, calibrated) and TOPMODEL (an hourly storm); its own [README](hydrology/README.md) compares the two
- `simulations/`: landscape evolution modelling: a synthetic mountain range at steady state, then responding to faster uplift
- `python_binding_examples/`: using the lsdtt3 Python bindings directly from Python, without parameter files

## Notebooks

Each notebook installs everything it needs in its first few cells, so you can open any of them directly in Colab:

- the lsdtt3 command-line programs from the [latest lsdtt3 release](https://github.com/LSDtopotools/lsdtt3/releases/latest);
- for the maps, condacolab and PyGMT from conda-forge and [lsdviztools3](https://pypi.org/project/lsdviztools3/) from PyPI. The field-point notebook draws its plots with matplotlib only, and installs neither;
- in `python_binding_examples/`, the [lsdtt3 Python package](https://pypi.org/project/lsdtt3/) from PyPI instead of the release (Python 3.12 or later). It contains the same command-line programs as well as the Python bindings.

| Notebook | What it does | |
|---|---|---|
| `surface_metrics/glencoe_hillshade_slope.ipynb` | Downloads a DEM around Glencoe, Scotland, computes a hillshade and topographic gradient, and maps them | [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/LSDtopotools/lsdtt3_notebooks/blob/main/surface_metrics/glencoe_hillshade_slope.ipynb) |
| `channel_extraction/apennines_channel_extraction.ipynb` | Downloads a DEM of the Apennine valleys south of Bologna, Italy, extracts the channel network and plots it by stream order over a hillshade | [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/LSDtopotools/lsdtt3_notebooks/blob/main/channel_extraction/apennines_channel_extraction.ipynb) |
| `channel_extraction/sierra_de_gador_chi_analysis.ipynb` | Extracts four basins in the Sierra de Gádor, Spain, and makes basin maps, long profiles, chi plots with fitted segments (ksn) and a channel network map | [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/LSDtopotools/lsdtt3_notebooks/blob/main/channel_extraction/sierra_de_gador_chi_analysis.ipynb) |
| `channel_extraction/your_area_basin_profiles.ipynb` | Upload your own area polygon and outlet points (GeoPackages), then extract the basins, their channels and long profiles. Example inputs are in `channel_extraction/example_data/` | [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/LSDtopotools/lsdtt3_notebooks/blob/main/channel_extraction/your_area_basin_profiles.ipynb) |
| `chi_analysis/salmon_river_chi_concavity_knickpoints.ipynb` | Downloads a 10 m USGS 3DEP DEM where the South Fork joins the main Salmon River (Mackay Bar, Idaho), takes every complete basin draining into the two rivers, finds the concavity index (m/n) of each with a disorder scan and bootstrap uncertainty, and makes a locator map, a basin map, stacked chi plots, k<sub>sn</sub> maps (continuous and in natural-breaks classes) and maps and profiles of the major knickpoints. Installs lsdviztools3 from PyPI and the latest lsdtt3 release | [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/LSDtopotools/lsdtt3_notebooks/blob/main/chi_analysis/salmon_river_chi_concavity_knickpoints.ipynb) |
| `landscape_transience/common_analyses_to_check_for_transience.ipynb` | Common checks for landscape transience in Calabria, Italy: gradient and curvature maps, a gradient histogram, basins, chi and long profiles, a swath profile and a ksn map (the lsdtt3 version of an lsdtt2 teaching notebook) | [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/LSDtopotools/lsdtt3_notebooks/blob/main/landscape_transience/common_analyses_to_check_for_transience.ipynb) |
| `lithology/upper_tweed_lithology_and_topography.ipynb` | Downloads a 30 m Copernicus DEM of the upper Tweed (Southern Uplands of Scotland, about 980 km² above the Ettrick Water) and its geological map from Macrostrat (BGS 1:625k) with `lsdtt-fetch-lithology`, finds the catchment's concavity with a disorder scan, computes k<sub>sn</sub> split by lithologic unit, and makes a network map with a locator, a labelled geological map, a k<sub>sn</sub> map in five classes, and charts of k<sub>sn</sub>, polyfit hillslope gradient, curvature and elevation by unit | [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/LSDtopotools/lsdtt3_notebooks/blob/main/lithology/upper_tweed_lithology_and_topography.ipynb) |
| `channel_cross_sections/whiteadder_cross_sections.ipynb` | Traces the Whiteadder Water (Lammermuir Hills, Scotland) downstream from the Whiteadder Reservoir along OS Open Rivers with `lsdtt-fetch-river-lines` (bridging a gap below the dam), places five sites at 1, 3, 5, 7 and 9 km with cross-section lines perpendicular to the river, maps the catchment, river and lidar tiles over a 30 m hillshade with a locator inset, downloads a 1 km tile of 1 m Scottish lidar around each site, takes a swath profile across the valley at each with `lsdtt-swath-profile`, and reads, plots and exports the swaths with pandas | [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/LSDtopotools/lsdtt3_notebooks/blob/main/channel_cross_sections/whiteadder_cross_sections.ipynb) |
| `floodplains_and_valleys/ohio_river_floodplain_widths.ipynb` | Downloads a 10 m USGS 3DEP DEM of the Ohio River valley around Moundsville, West Virginia, maps the floodplain with the Clubb et al. (2017) HAND and gradient thresholds (chosen automatically, then set by hand), and measures floodplain widths on cross sections down every valley | [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/LSDtopotools/lsdtt3_notebooks/blob/main/floodplains_and_valleys/ohio_river_floodplain_widths.ipynb) |
| `dealing_with_field_point_data/lammermuir_combining_river_and_point_data.ipynb` | Downloads 1 m Scottish lidar (phase 3) of the Kilmade Burn, Lammermuir Hills, computes drainage area, chi and a 20 m along-channel gradient, simulates 30 field sites (channel width, d50, d84) with GPS errors of 3–10 m, snaps them to the channel network with `run_channel_point_attributes`, joins chi, checks the snapping against the true positions, fits width against drainage area, and compares the along-channel gradient with a 4 m polyfit gradient on maps | [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/LSDtopotools/lsdtt3_notebooks/blob/main/dealing_with_field_point_data/lammermuir_combining_river_and_point_data.ipynb) |
| `hydrology/s_hype_simulation.ipynb` | Runs a simple S-HYPE rainfall–runoff simulation of Ettrick Water (NRFA gauge 21017, Southern Uplands of Scotland): gets the gauge and its daily flows from the National River Flow Archive, a 30 m DEM, and daily rainfall and temperature from Open-Meteo, builds the sub-basin from the DEM, maps the catchment and its channel network, runs `lsdtt-distributed-hydrology` with uniform land use, soil and parameters, compares the simulated and gauged flows, and calibrates seven parameters with SPOTPY in a few minutes, checked on a year the calibration did not see, and tests a second soil class along the channel network | [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/LSDtopotools/lsdtt3_notebooks/blob/main/hydrology/s_hype_simulation.ipynb) |
| `hydrology/topmodel_storm.ipynb` | Runs TOPMODEL on every 30 m pixel of the same Ettrick Water catchment through the October 2021 flood, at hourly steps: hourly rainfall from Open-Meteo, the catchment cut from the DEM, the hydrograph against the NRFA daily flows, and maps of the saturation deficit and saturated area at four times during the storm | [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/LSDtopotools/lsdtt3_notebooks/blob/main/hydrology/topmodel_storm.ipynb) |
| `simulations/steady_state_and_uplift_increase.ipynb` | Builds a synthetic mountain range with `lsdtt-lem` (stream power erosion and hillslope diffusion), snaps it to steady state, maps its hillshade, channel network and gradient with the long and chi profiles of the largest basin, then increases the uplift rate and shows the landscape responding in snapshots every 200,000 years | [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/LSDtopotools/lsdtt3_notebooks/blob/main/simulations/steady_state_and_uplift_increase.ipynb) |
| `python_binding_examples/lsdtt3_bindings_quickstart.ipynb` | Uses the lsdtt3 Python bindings (no parameter files) on the Aspromonte and Serre, Calabria: downloads a DEM with `lsdtt3.fetch_dem`, maps gradient (m/m) and the channel network, extracts six basins, and makes a slope–area plot, chi profiles and a k<sub>sn</sub> map, all drawn with lsdviztools3 | [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/LSDtopotools/lsdtt3_notebooks/blob/main/python_binding_examples/lsdtt3_bindings_quickstart.ipynb) |

## Author

Simon M. Mudd

## License

The notebooks are MIT licensed: see [LICENSE](LICENSE). lsdtt3 is licensed AGPL-3.0-or-later and lsdviztools3 MIT; see their repositories.
