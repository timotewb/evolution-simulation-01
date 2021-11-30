# docker image build -t evolution-simulation-01 .
# cd ../../ # into evolution-simulation-01 dir
# docker run -v "$(pwd):/home/jovyan/code" -p 18888:8888 --name evolution-simulation-01 evolution-simulation-01
# docker run -v "%cd%:/home/jovyan/code" -p 18888:8888 --name evolution-simulation-01 evolution-simulation-01

FROM jupyter/base-notebook:python-3.9.7

COPY --chown=jovyan:users requirements.txt /tmp/

USER root
RUN sudo apt-get update
RUN sudo apt-get install -y libpq-dev
RUN sudo apt-get install -y gcc
RUN sudo apt-get install -y htop

RUN pip install --requirement /tmp/requirements.txt && \
    fix-permissions $CONDA_DIR && \
    fix-permissions /home/$NB_USER
