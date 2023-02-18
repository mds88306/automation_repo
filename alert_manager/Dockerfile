FROM ubuntu
RUN apt-get update -y && mkdir -p /etc/alertmanager/ /alertmanager/
RUN apt-get install wget curl -y
RUN wget https://github.com/prometheus/alertmanager/releases/download/v0.25.0/alertmanager-0.25.0.linux-amd64.tar.gz
RUN tar -xvzf alertmanager-0.25.0.linux-amd64.tar.gz
RUN cp /alertmanager-0.25.0.linux-amd64/alertmanager.yml /etc/alertmanager/
RUN cp /alertmanager-0.25.0.linux-amd64/alertmanager /bin/
RUN cp /alertmanager-0.25.0.linux-amd64/amtool /bin/
WORKDIR /alertmanager
EXPOSE 9093
ENTRYPOINT [ "/bin/alertmanager" ]
CMD [ "--config.file=/etc/alertmanager/alertmanager.yml", \
      "--storage.path=/alertmanager" ]
