FROM python:3.8.0
LABEL maintainer "Kaoru Yamaoka <kaoru.yamaoka@gmail.com>"

#install jupyter lab
RUN pip install --upgrade pip && pip install jupyterlab

ENV LD_LIBRARY_PATH="/usr/local/lib:$LD_LIBRARY_PATH"
COPY embree.bash /work/
WORKDIR /work
RUN /bin/bash embree.bash

# install required python libraries
COPY requirements.txt /work/
WORKDIR /work
RUN pip install -r requirements.txt
RUN jupyter serverextension enable --py jupyterlab

# run
WORKDIR /work
CMD ["/bin/bash"]