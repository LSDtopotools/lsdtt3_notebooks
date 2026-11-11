# lsdtt3_notebooks

These are some Jupyter notebooks for running basic topographic analysis on [Google Colab](https://colab.research.google.com/) using **lsdtt3** (LSDTopoTools v3) and **lsdviztools3**.

**Both of these packages are in (for the time being) in development so these should be considered experimental**

## Contents

- `setting_up_and_getting_data/`: installing lsdtt3, lsdviztools3 and PyGMT on Colab, and downloading DEMs
- `channel_extraction/`: extracting channel networks
- `chi_analysis/`: chi analysis: concavity from the disorder method, channel steepness (k<sub>sn</sub>) and knickpoints
- `surface_metrics/`: computing surface metrics
- `landscape_transience/`: common analyses for checking whether a landscape is transient
- `floodplains_and_valleys/`: mapping floodplains and measuring valley widths
- `python_binding_examples/`: using the lsdtt3 Python bindings directly from Python, without parameter files

## Notebooks

Each notebook installs everything it needs (condacolab, PyGMT, lsdviztools3 and the lsdtt3 binaries) in its first few cells, so you can open any of them directly in Colab. The notebooks in `python_binding_examples/` install the lsdtt3 Python wheel (Linux x86_64, Python 3.13) instead of the binaries.

| Notebook | What it does | |
|---|---|---|
| `setting_up_and_getting_data/setting_up_lsdtt3.ipynb` | Sets up the Colab environment and downloads a DEM of the Sierra Nevada, Spain | [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/LSDtopotools/lsdtt3_notebooks/blob/main/setting_up_and_getting_data/setting_up_lsdtt3.ipynb) |
| `surface_metrics/glencoe_hillshade_slope.ipynb` | Downloads a DEM around Glencoe, Scotland, computes a hillshade and topographic gradient, and maps them | [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/LSDtopotools/lsdtt3_notebooks/blob/main/surface_metrics/glencoe_hillshade_slope.ipynb) |
| `channel_extraction/apennines_channel_extraction.ipynb` | Downloads a DEM of the Apennine valleys south of Bologna, Italy, extracts the channel network and plots it by stream order over a hillshade | [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/LSDtopotools/lsdtt3_notebooks/blob/main/channel_extraction/apennines_channel_extraction.ipynb) |
| `channel_extraction/sierra_de_gador_chi_analysis.ipynb` | Extracts four basins in the Sierra de Gádor, Spain, and makes basin maps, long profiles, chi plots with fitted segments (ksn) and a channel network map | [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/LSDtopotools/lsdtt3_notebooks/blob/main/channel_extraction/sierra_de_gador_chi_analysis.ipynb) |
| `channel_extraction/your_area_basin_profiles.ipynb` | Upload your own area polygon and outlet points (GeoPackages), then extract the basins, their channels and long profiles. Example inputs are in `channel_extraction/example_data/` | [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/LSDtopotools/lsdtt3_notebooks/blob/main/channel_extraction/your_area_basin_profiles.ipynb) |
| `chi_analysis/salmon_river_chi_concavity_knickpoints.ipynb` | Downloads a 10 m USGS 3DEP DEM where the South Fork joins the main Salmon River (Mackay Bar, Idaho), takes every complete basin draining into the two rivers, finds the concavity index (m/n) of each with a disorder scan and bootstrap uncertainty, and makes a basin map, stacked chi plots, a k<sub>sn</sub> map and maps and profiles of the major knickpoints. Installs lsdviztools3 from PyPI and the latest lsdtt3 release | [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/LSDtopotools/lsdtt3_notebooks/blob/main/chi_analysis/salmon_river_chi_concavity_knickpoints.ipynb) |
| `landscape_transience/common_analyses_to_check_for_transience.ipynb` | Common checks for landscape transience in Calabria, Italy: gradient and curvature maps, a gradient histogram, basins, chi and long profiles, a swath profile and a ksn map (the lsdtt3 version of an lsdtt2 teaching notebook) | [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/LSDtopotools/lsdtt3_notebooks/blob/main/landscape_transience/common_analyses_to_check_for_transience.ipynb) |
| `floodplains_and_valleys/ohio_river_floodplain_widths.ipynb` | Downloads a 10 m USGS 3DEP DEM of the Ohio River valley around Moundsville, West Virginia, maps the floodplain with the Clubb et al. (2017) HAND and gradient thresholds (chosen automatically, then set by hand), and measures floodplain widths on cross sections down every valley | [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/LSDtopotools/lsdtt3_notebooks/blob/main/floodplains_and_valleys/ohio_river_floodplain_widths.ipynb) |
| `python_binding_examples/lsdtt3_bindings_quickstart.ipynb` | Uses the lsdtt3 Python bindings (no parameter files) on the Aspromonte and Serre, Calabria: downloads a DEM with `lsdtt3.fetch_dem`, maps gradient (m/m) and the channel network, extracts six basins, and makes a slope–area plot, chi profiles and a k<sub>sn</sub> map, all drawn with lsdviztools3 | [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/LSDtopotools/lsdtt3_notebooks/blob/main/python_binding_examples/lsdtt3_bindings_quickstart.ipynb) |

## Author

Simon M. Mudd

## License

MIT. See [LICENSE](LICENSE).
