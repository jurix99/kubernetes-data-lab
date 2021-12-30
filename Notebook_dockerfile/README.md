### Create a docker file for python development
This image is based on an official jupyter image.
Already installed:
    - python
    - jupyter
    - Basic Libraries
    - Sparks

The environment is a debian.
Mamba is installed to download libraries using conda.
So create a DockerFile running *mamba install* to download TensorFlow and *MongoDB*.
```Dockerfile
FROM jupyter/pyspark-notebook

# Install Tensorflow
RUN mamba install --quiet --yes \
    'tensorflow' && \
    mamba clean --all -f -y && \
    fix-permissions "${CONDA_DIR}" && \
    fix-permissions "/home/${NB_USER}"

# Install PyTorch
RUN mamba install -- quiet --yes \
    'pytorch' && \
    mamba clean --all -f -y && \
    fix-permissions "${CONDA_DIR}" && \
    fix-permissions "/home/${NB_USER}"
```

```shell
docker build . -f Deeplearning-Notebook.txt -t deeplearning-notebook
```

```shell
docker run -p 8888:8888 deeplearning-notebook
```