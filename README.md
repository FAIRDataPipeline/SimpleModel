# rSimpleModel

A simple example of an SEIRS epidemiological model using the [FAIR Data Pipeline](https://fairdatapipeline.github.io).

## Installing the command line tools

If you don't already have the registry initialised and the `fair` command line tool configured, then you need to install that next - see [here](https://github.com/FAIRDataPipeline/FAIR-CLI#installation) for more details. Briefly, with python and poetry (`pip install poetry`) installed:


```sh
git clone https://github.com/FAIRDataPipeline/FAIR-CLI.git
cd FAIR-CLI
poetry install
poetry shell
```

You are now running in a new shell created by `poetry` that has a copy of the `fair` executable in its path.

## Configuring the registry and running the example in this repo

Install the [`rDataPipeline`](https://github.com/FAIRDataPipeline/rDataPipeline) package:

```R
install.packages(devtools)
devtools::install_github("FAIRDataPipeline/rDataPipeline")
library(rDataPipeline)
```

Download and install the [rSimpleModel](https://github.com/FAIRDataPipeline/rSimpleModel) code. In some suitable directory, clone the git repo:

[rSimpleModel](https://github.com/FAIRDataPipeline/rSimpleModel) code. In some suitable directory, clone the git repo:

```sh
git clone https://github.com/FAIRDataPipeline/rSimpleModel.git
cd rSimpleModel
```

At this point you can configure `fair` to run in this repo. Either run:

```sh
fair init
```

And fill in your own details, or simply run:

```sh
fair init --ci
```

In this case the CLI will initialise the repo with dummy values that are used for continuous integration testing.

Finally you can run the example!

## Running the example

This is easy. The user configuration script for running the R SEIRS model can be found inside this repo - [inst/extdata/SEIRSconfig.yaml](https://raw.githubusercontent.com/FAIRDataPipeline/rSimpleModel/main/inst/extdata/SEIRSconfig.yaml) - and for this self-contained example, it includes all of the information to register the input data that the model needs, so that you don't have to be connected to a registry that already knows about it. The code can be executed by first ensuring that all of the input data is available in the local registry (using `fair pull`) and then running the code (using `fair run`). So:

```sh
fair pull inst/extdata/SEIRSconfig.yaml
fair run inst/extdata/SEIRSconfig.yaml
```

That's it! If you go to the local registry in your browser now (by default at http://localhost:8000), you should see the input and output data recorded in the registry.
