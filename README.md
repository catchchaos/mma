# Multiscale Multifractal Analysis
Multiscale multifractal analysis (MMA) (Gierałtowski et al., 2012) is a time series analysis method, designed to describe scaling properties of fluctuations within the signal analyzed. The main result of this procedure is the so called Hurst surface h(q,s) , which is a dependence of the local Hurst exponent h (fluctuation scaling exponent) on the multifractal parameter q (Kantelhardt et al., 2002) and the scale of observation s (data window width). For more information, check out [this link](https://physionet.org/physiotools/mma/)

Implementation is in R. Only standard libraries that come with the R release were used, so no new packages need to be installed.

### Procedure

* Initialise parameters including range of scales and fractal parameters. We can't have q value = 0 because we take power of 1/q at one point
* Read time series data from file, file format - numbers alone, one per line in text file
* Find profile of the signal by calculating cumulative sum for the whole series
* Reshape the profiled signal into a matrix, so that we can extract segments
* Obtain fits for all bases and calculate the mean variance for the same
* Hence calculate the fluctuations from the obtained mean values
* Calculate log values of scales and fluctuations, for easy reporesentation in a graph
* Calculate the hurst exponent to be stored for each unique pair of (q,s)
* Reshape the hurst exponent values to a matrix so that we can plot it as a surface
* Generate the desired number of colors from this palette and compute the z-value at the facet centres. Recode facet z-values into color indices
* 3D Plot is obtained
