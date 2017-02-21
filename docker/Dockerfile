FROM tensorflow/tensorflow:latest-py3

RUN apt-get update && apt-get install -y --no-install-recommends \
    git wget libhdf5-dev && \
    apt-get clean && \
    rm -rf /var/lib/apt/lists/*
# Python
RUN pip --no-cache-dir install \
    pydicom \
    ipdb \
    pytest \
    pytest-cov \
    python-coveralls \
    coverage==3.7.1 \
    pytest-xdist \
    pep8 \
    pytest-pep8 \
    pydot_ng \
#    Pillow \
#    scikit-learn \
#    notebook \
#    pandas \
#    matplotlib \
    nose \
    pyyaml \
    six \
    h5py

RUN pip --no-cache-dir install git+git://github.com/Theano/Theano.git

RUN pip --no-cache-dir install git+git://github.com/fchollet/keras.git

WORKDIR /src

EXPOSE 8888

CMD jupyter notebook --port=8888 --ip=0.0.0.0
