FROM circleci/python:3.6-stretch

RUN sudo apt-get update \
  && sudo apt-get install -y \
         groff-base \
         less \
         python \
         python-pip \
         python-dev \
  && sudo pip install awscli

ADD .aws/ /home/circleci/.aws
