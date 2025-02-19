# cmip7-aerosol-paper

Additional material to reproduce Figures 12, 13, and 14 of the results of
Fiedler et al. (2025) with ESMValTool.

## Quick Start

To reproduce these results, a [development
installation](https://docs.esmvaltool.org/en/latest/quickstart/installation.html#install-from-source)
of ESMValTool and ESMValCore is necessary using the [main
branch](https://github.com/ESMValGroup/ESMValTool/tree/main) of ESMValTool and
the [icon-xpp branch](https://github.com/ESMValGroup/ESMValCore/tree/icon-xpp)
of ESMValCore. The new features will be released with ESMValTool v2.13.0 in the
future. Once this is done, a regular installation of ESMValTool will be
sufficient.

Before ESMValTool can be used, input data need to be acquired:

- CMIP6 data: can be automatically downloaded from the ESGF using the option
  `search_esgf: when_missing`, see details
  [here](https://docs.esmvaltool.org/en/latest/input.html#models).
- Observational data: needs to be downloaded and CMORized by the user using
  downloader and CMORizer scripts provided by ESMValTool, see details
  [here](https://docs.esmvaltool.org/en/latest/input.html#observations).
- ICON data: needs to be downloaded from the source specified in the
  publication.

As a final step before running ESMValTool, it needs to be
[configured](https://docs.esmvaltool.org/en/latest/quickstart/configuration.html),
i.e.:

```bash
esmvaltool config get_config_user
```

This will download the configuration file to
`~/.config/esmvaltool/config-user.yml`. Add/modify the following lines:

```yml
output_dir: ~/esmvaltool_output  # path where ESMValTool output is written
search_esgf: when_missing  # enable automatic downloads for CMIP data
download_dir: ~/climate_data  # directory where downloaded data is stored

rootpath:  # paths to input data
  OBS:
    /path/to/observational_data: default
  OBS6:
    /path/to/observational_data: default
  native6:
    /path/to/observational_data: default
  ICON:
    /path/to/icon_data: default
```

For various HPC centers (e.g., DKRZ's Levante, JASMIN, etc.), predefined
configurations exist, which are supplied with the [default
configuration](https://docs.esmvaltool.org/en/latest/quickstart/configuration.html).

Finally, ESMValTool recipes can be run with

```bash
esmvaltool run /path/to/recipe.yml
```

## Contents

### Figure files (`figs/`)

Contains raw figures and corresponding netCDF, provenance and citation files.

### ESMValTool recipes (`recipes/`)

Contains [ESMValTool
recipes](https://docs.esmvaltool.org/projects/ESMValCore/en/v2.11.1/recipe/index.html)
used to reproduce figures of the paper.
