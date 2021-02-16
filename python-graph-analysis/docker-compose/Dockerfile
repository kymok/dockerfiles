FROM ubuntu:20.04
LABEL maintainer "Kaoru Yamaoka <kaoru.yamaoka@gmail.com>"
ENV DEBIAN_FRONTEND=noninteractive

RUN apt-get update && \
apt-get install -y python3-pip && \
rm -rf /var/lib/apt/lists/*

#install jupyter lab
RUN pip3 install --upgrade pip && pip3 install jupyterlab

# install dependencies
# libspatialindex (osmnx)
# python3-seleniym (altair)
RUN apt-get update && \
apt-get install -y libspatialindex-dev && \
apt-get install -y python3-selenium && \
rm -rf /var/lib/apt/lists/*

# install required python libraries
COPY requirements.txt /work/
WORKDIR /work
RUN pip3 install -r requirements.txt
RUN jupyter serverextension enable --py jupyterlab

# run
WORKDIR /work
CMD ["/bin/bash"]
