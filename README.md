# datadive 2018-02-07


### UVA DATADIVE 2018-02-07
In preparation for Nathan's session:  
https://github.com/NathanCDay/data_dive

Pre-requisites for Cville Crime Data-Dive session: 
```R
library(magrittr)
library(tidyverse) # devtools::install_github("tidyverse/ggplot2")
library(geojsonio)
library(ggmap)
library(sf)
library(viridis)
library(spdep)
library(tidycensus)
```

Register for a census api key:  http://api.census.gov/data/key_signup.html
```R
#run in your R session, after loading tidycensus:
census_api_key('your_private_key')
```


Installing both R/Rstudio and these packages manually can be challenging, depending on your operating system and configuration (especially since many depend on heterogeneous C libraries). 

If you don't mind the extra space, then starting from an existing docker image removes these headaches. 

In this case, I've started from rocker/ropensci and added 3 additional packages (ggmap, tidycensus, github_ggplot2). See the dockerfile for recipe. I've uploaded the built image to dockerhub and tagged the image with the datadive date for version control. If you pull from this, make sure to include the date as tag:  
```bash
docker pull jfx319/datadive:2018-02-07
```

### EXAMPLE USAGE

Assuming you have [docker installed](https://docs.docker.com/install), run:

```bash
docker run -d -p 8787:8787 -v '/mylocalharddrive/datadive:/home/jfx319/datadive' -w /home/jfx319/datadive -e USER=jfx319 -e PASSWORD=mypassword jfx319/datadive:2018-02-07
```
where `/mylocalharddrive/datadive` is the actual folder on your computer  
and `/home/jfx319/datadive` is the desired folder in the container's Rstudio  
and `jfx319` as well as `mypassword` are your username and password

To understand or customize these options, refer to [docker commands](https://www.linuxfoundation.org/blog/basic-commands-for-performing-docker-container-operations/) and the [rocker wiki](https://github.com/rocker-org/rocker/wiki/Using-the-RStudio-image)

Now go to your browser and open your ip address or localhost: 
```
127.0.0.1:8787
```

When finished, make sure to save your work (if you didn't mount a local folder); and stop your container: 
```
docker stop <container_id>
```
