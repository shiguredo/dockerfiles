FROM circleci/python:2.7-stretch

LABEL maintainer="namao.takeshi@gmail.com"

RUN sudo apt-get update \
  && sudo apt-get upgrade -y \
  && sudo apt-get install -y \
         lsb-release \
         groff-base \
         less \
         python \
         python-dev \
         python-pip

RUN export CLOUD_SDK_REPO="cloud-sdk-$(lsb_release -c -s)" \
  && echo "deb http://packages.cloud.google.com/apt $CLOUD_SDK_REPO main" | sudo tee -a /etc/apt/sources.list.d/google-cloud-sdk.list \
  && curl https://packages.cloud.google.com/apt/doc/apt-key.gpg | sudo apt-key add - \
  && sudo apt-get update \
  && sudo apt-get install google-cloud-sdk

RUN sudo sed -i -e 's/true/false/' /usr/lib/google-cloud-sdk/lib/googlecloudsdk/core/config.json
