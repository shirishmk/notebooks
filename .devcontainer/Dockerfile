FROM continuumio/miniconda3

# Install necessary packages
RUN apt-get update && apt-get install -y \
    wget \
    bzip2 \
    ca-certificates \
    curl \
    git \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/*

# Create a Conda environment
COPY environment.yml /tmp/environment.yml
RUN conda env create -f /tmp/environment.yml && \
    conda clean -a && \
    echo "source activate devcontainer" > ~/.bashrc

# Install Cling and Xeus-Cling
RUN conda install -c conda-forge cling xeus-cling

# Set the default environment
ENV PATH /opt/conda/envs/devcontainer/bin:$PATH
