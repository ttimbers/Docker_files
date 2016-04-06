# mmp-dyf-skat

## Full Description
Docker image for environment used for SKAT analysis of Million Mutation Project strains dye-filling phenotypes reported in Timbers et al. http://biorxiv.org/content/early/2015/10/22/027540

## Docker Pull Command
docker pull ttimbers/mmp-dyf-skat

## Owner
Tiffany Timbers ([ttimbers](https://hub.docker.com/u/ttimbers/) on Docker Hub)

## Notes:

To test this locally on OSX or Windows you need > 2 GB of memory allocated to virtualbox.
To do this, I created another Docker machine using the following commands in the Shell:

~~~
# create new Docker machine
docker-machine create --driver virtualbox --virtualbox-disk-size "100000" --virtualbox-memory "7168" Large

# run docker command ps
docker $(docker-machine config Large) ps

# create docker image from file
docker $(docker-machine config Large) build -t mmp-dyf-skat .

# run docker image
docker $(docker-machine config Large) run -it mmp-dyf-skat
~~~