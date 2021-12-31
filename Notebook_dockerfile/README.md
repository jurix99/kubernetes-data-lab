# Create a docker file for python development

This image is based on an official jupyter image.
Already installed:
+ python
+ jupyter
+ Basic Libraries

The environment is a debian.  
[Mamba](https://github.com/mamba-org/mamba) is installed to download libraries using conda. 
   
So create a DockerFile running `mamba install` to download **MongoDB**, so we are adding PyMongo

```Dockerfile
FROM jupyter/scipy-notebook

# Defining the shell commands prefixes
SHELL ["/bin/bash", "-o", "pipefail", "-c"]

# Using mamba

# Install Pymongo
RUN mamba install --quiet --yes \
    'pymongo' && \
    mamba clean --all -f -y && \
    fix-permissions "${CONDA_DIR}" && \
    fix-permissions "/home/${NB_USER}"
```
Then, we are using `docker build` to build the image, `-t` to specify the name of the created image.
```shell
docker build . -f Notebook_dockerfile/Deeplearning-Notebook.txt -t sebjul06/deeplearning-notebook
```
And now, we are running the image with `docker run`, `-p` to map the virtual port of the container with our physical port.
```shell
docker run -p 8888:8888 deeplearning-notebook
```