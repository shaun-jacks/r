FROM rocker/binder

## Copies your repo files into the Docker Container
USER root

RUN apt-get -y install software-properties-common && apt-get -y update
RUN add-apt-repository ppa:marutter/c2d4u3.5 && apt-get -y update


RUN apt-get -y install r-cran-lme4 && apt-get -y install r-cran-nlme

COPY . ${HOME}
RUN chown -R ${NB_USER} ${HOME}

## Become normal user again
USER ${NB_USER}

## Run an install.R script, if it exists.
RUN if [ -f install.R ]; then R --quiet -f install.R; fi
