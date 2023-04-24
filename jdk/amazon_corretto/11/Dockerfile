FROM ubuntu:22.04

RUN apt-get update && \
    apt-get install -y curl gnupg2 software-properties-common

RUN curl -s https://apt.corretto.aws/corretto.key | apt-key add - && \
    add-apt-repository 'deb https://apt.corretto.aws stable main' && \
    apt-get update; apt-get install -y java-11-amazon-corretto-jdk && \
    java --version
