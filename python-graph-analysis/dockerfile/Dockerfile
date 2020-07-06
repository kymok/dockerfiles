FROM python:3.8.0
LABEL maintainer "Kaoru Yamaoka <kaoru.yamaoka@gmail.com>"

#install jupyter lab
RUN pip install --upgrade pip && pip install jupyterlab

# install graph-tool
RUN echo "deb [ arch=amd64 ] https://downloads.skewed.de/apt buster main" >> /etc/apt/sources.list \
&& apt-key adv --keyserver keys.openpgp.org --recv-key 612DEFB798507F25 \
&& apt-get update \
&& apt-get install -y python3-graph-tool \
&& rm -rf /var/lib/apt/lists/*

# install libspatialindex (dependency for osmnx)
RUN apt-get update && apt-get install -y libspatialindex-dev && rm -rf /var/lib/apt/lists/*

# install required python libraries
COPY requirements.txt /app/
WORKDIR /app
RUN pip install -r requirements.txt
RUN jupyter serverextension enable --py jupyterlab

# run
WORKDIR /app
CMD ["/bin/bash"]