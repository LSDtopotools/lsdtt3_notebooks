# lsdtt3_notebooks

These are some Jupyter notebooks for running basic topographic analysis on [Google Colab](https://colab.research.google.com/) using **lsdtt3** (LSDTopoTools v3) and **lsdviztools3**.

**Both of these packages are in (for the time being) in development so these should be considered experimental**

## Contents

- `setting_up_and_getting_data/`: installing lsdtt3, lsdviztools3 and PyGMT on Colab, and downloading DEMs
- `channel_extraction/`: extracting channel networks
- `surface_metrics/`: computing surface metrics

## Notebooks

Each notebook installs everything it needs (condacolab, PyGMT, lsdviztools3 and the lsdtt3 binaries) in its first few cells, so you can open any of them directly in Colab.

| Notebook | What it does | |
|---|---|---|
| `setting_up_and_getting_data/setting_up_lsdtt3.ipynb` | Sets up the Colab environment and downloads a DEM of the Sierra Nevada, Spain | [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/LSDtopotools/lsdtt3_notebooks/blob/main/setting_up_and_getting_data/setting_up_lsdtt3.ipynb) |
| `surface_metrics/glencoe_hillshade_slope.ipynb` | Downloads a DEM around Glencoe, Scotland, computes a hillshade and topographic gradient, and maps them | [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/LSDtopotools/lsdtt3_notebooks/blob/main/surface_metrics/glencoe_hillshade_slope.ipynb) |
| `channel_extraction/apennines_channel_extraction.ipynb` | Downloads a DEM of the Apennine valleys south of Bologna, Italy, extracts the channel network and plots it by stream order over a hillshade | [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/LSDtopotools/lsdtt3_notebooks/blob/main/channel_extraction/apennines_channel_extraction.ipynb) |
| `channel_extraction/sierra_de_gador_chi_analysis.ipynb` | Extracts four basins in the Sierra de Gádor, Spain, and makes basin maps, long profiles, chi plots with fitted segments (ksn) and a channel network map | [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/LSDtopotools/lsdtt3_notebooks/blob/main/channel_extraction/sierra_de_gador_chi_analysis.ipynb) |
| `channel_extraction/your_area_basin_profiles.ipynb` | Upload your own area polygon and outlet points (GeoPackages), then extract the basins, their channels and long profiles. Example inputs are in `channel_extraction/example_data/` | [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/LSDtopotools/lsdtt3_notebooks/blob/main/channel_extraction/your_area_basin_profiles.ipynb) |

## Author

Simon M. Mudd

## License

MIT. See [LICENSE](LICENSE).
