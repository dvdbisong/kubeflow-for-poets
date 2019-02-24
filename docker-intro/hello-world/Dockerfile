ARG UBUNTU_VERSION=16.04

FROM ubuntu:${UBUNTU_VERSION} as base

# python 3
ARG PYTHON=python3
ARG PIP=pip3

# See http://bugs.python.org/issue19846
ENV LANG C.UTF-8

RUN apt-get update && apt-get install -y \
    git \
    ${PYTHON} \
    ${PYTHON}-pip

RUN ${PIP} --no-cache-dir install --upgrade \
    pip \
    setuptools

# Some TF tools expect a "python" binary
RUN ln -s $(which ${PYTHON}) /usr/local/bin/python 

ARG TF_PACKAGE=tensorflow
ARG TF_PACKAGE_VERSION=
RUN ${PIP} install ${TF_PACKAGE}${TF_PACKAGE_VERSION:+==${TF_PACKAGE_VERSION}}

RUN ${PIP} install jupyter matplotlib jupyter_http_over_ws pandas matplotlib sklearn
RUN jupyter serverextension enable --py jupyter_http_over_ws

RUN mkdir /tf && chmod -R a+rwx /tf/
WORKDIR /tf
RUN git clone https://github.com/dvdbisong/ieee-ompi-ml-workshop.git
WORKDIR /tf
EXPOSE 8888

RUN ${PYTHON} -m ipykernel.kernelspec

CMD ["bash", "-c", "source /etc/bash.bashrc && jupyter notebook --notebook-dir=/tf --ip 0.0.0.0 --no-browser --allow-root"]