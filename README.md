# Finding the Climate Change

This Jupyter / PySpark notebook tries to support the theory of climate change by analysing raw weather data. The basic idea is not to rely on
readily analyzed reports but to find relevant information by only using raw weather measurements.

The notebook will use publicly available data from the National Oceanic and Atmospheric Administration (NOAA). 


## Disclaimer

I am neither an expert for meteorology nor for climate models. I will try to use common sense to gather some insights. Eventually this was part of my idea: Everyone who has some experience with working with data should be able to perform some conclusions on the climate change given a detailed enough data set.

I will add some remarks where I know that things are not correct. As far as I know real expert would go down a completely different route and build a weather model from the given measurements and then interpolate the weather evenly across the whole earth. This is completely out of scope of this article, we instead will use simple averages of the measurements per country.


## Prerequisistes

Before following the notebook, you need to setup an appropriate environment. This includes both the correct software stack and enough hardware to work with the data.

### Software requirements

This notebook requires Jupyter and PySpark. An `environment.yml` file for setting up an appropriate Anaconda environment is part of the repository. You can create an environment via

```sh
conda env create -n weather -f environment.yml
```
Then you can activate the environment and start the Jupyter Lab server via
```sh
conda activate weather
jupyter-lab  --ip=0.0.0.0 --port=8888  
```

### Hardware recommendations

The weather data is huge, it consists of 100GB compressed data. So a fast machine with lots of RAM and plenty of fast storage is recommended for following the analysis.
* Fast machine, many cores. I used a single machine with 20 cores with hyperthreading (i.e. 40 threads) with 64GB of RAM
* At least 300GB of free disk space (100 GB for NOAA archive, 50 GB for intermediate results and 150 GB for Spark scratch space)
* Working Jupyter Notebook with PySpark (I used 3.0, but 2.4 should also work fine)
