FROM ubuntu
RUN apt-get update -y && mkdir -p /node_exporter
RUN apt-get install wget curl -y
RUN wget https://github.com/prometheus/node_exporter/releases/download/v1.5.0/node_exporter-1.5.0.linux-amd64.tar.gz
RUN tar -xvzf node_exporter-1.5.0.linux-amd64.tar.gz
RUN cp /node_exporter-1.5.0.linux-amd64/node_exporter /bin/
WORKDIR /node_exporter
EXPOSE 9100
ENTRYPOINT ["/bin/node_exporter"]
