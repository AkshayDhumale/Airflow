FROM apache/airflow:2.8.0rc4-python3.11@sha256:3731e4942cdb08f51a9aef43f3dfc2de786c2cd93a65250a13b0ebac73185635

USER root

# Install OpenJDK-11
RUN apt-get update && \
    apt-get install -y openjdk-17-jdk && \
    apt-get install -y ant && \
    apt-get clean;

# Set JAVA_HOME
ENV JAVA_HOME /usr/lib/jvm/java-17-openjdk-amd64/

RUN export JAVA_HOME

USER airflow

COPY ./requirements.txt /

RUN pip install -r /requirements.txt

COPY --chown=airflow:root ./dags /opt/airflow/dags
