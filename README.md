# NHP_in_brazil 

This repository will contain relevant examples of using odin.dust and mcstate for defining and estimating a model of transmission in non-human primates. These examples are based on the SIR model shared with odin/odin.dust and mcstate packages.

You definitely want to read this: https://mrc-ide.github.io/mcstate/articles/sir_models.html 

# SIR example
This is almost exactly the same as the vignette for mcstate. Here we have 4 files in a folder- the index, compare, sir and example scripts. The index and compare are the same as the mcstate example and are functions to pick out the relevant points from the data/model, or, perform the likelihood/ observation process calculation respectively. The sir model is a susceptible-infectious-recovered model with a 1 day timestep as default. In the example.R script is where you find an example of running the particle filter on this model, and an example of estimating beta and gamma (transmission parameter and recovery parameter respectively) from dummy data (also taken from the MCstate package).

# SIR_temp example
This is almost identical to the above but the transmission parameter beta now depends nonlinearly on temperature. It means that rather than estimating beta directly, you estimate of the parameters of the function for how beta varies with temperature. This will be more useful as other regions/ municipalities are added.

# SIR temp nested example
This takes data from two populations, here we are assuming they are two regions or municipalities. The model itself is the same in the two regions but what varies is 1) temperature and 2) the temperature scaling. The nested approach assumes that there is going to be one or more parameters that vary across regions. The data is made up and the model is only run for a small number of iterations as an illustration.

# SIR temp multipatch example
Here we include a model that has multiple regions or populations. Then in the estimation all the parameters are the same but the temperature varies between regions. Again, the data is made up and the model is only estimated for a small number of iterations for illustration. 

# Human model connection example
Here we present an example of how a non-human primate model could be used to generate input for a version of the existing human model. A non-human primate SIR model similar to those in previous examples but incorporating a mortality term is run to generate SIR data. The infectious fraction of the NHP population (I/(S+I+R)) is then used to calculate the spillover force of infection affecting the human population as a function of time, via a simple linear calculation. The human model is then run with this input over the same period of time. The basic reproduction number R0 in both NHPs and humans is supplied as a function of time, so it can be constant or incorporate seasonal variation and/or variation from year to year.