FROM ubuntu
RUN apt-get update -y && mkdir -p /etc/prometheus/ /prometheus/
RUN apt-get install wget curl -y
RUN wget https://github.com/prometheus/prometheus/releases/download/v2.42.0/prometheus-2.42.0.linux-amd64.tar.gz
RUN tar -xvzf prometheus-2.42.0.linux-amd64.tar.gz
RUN mkdir -p /usr/share/prometheus/consoles  /usr/share/prometheus/console_libraries
RUN cp prometheus-2.42.0.linux-amd64/prometheus.yml /etc/prometheus/
RUN cp prometheus-2.42.0.linux-amd64/prometheus /bin/
RUN cp prometheus-2.42.0.linux-amd64/promtool /bin/
RUN cp -r prometheus-2.42.0.linux-amd64/consoles/ /usr/share/consoles/
RUN cp -r prometheus-2.42.0.linux-amd64/console_libraries/ /usr/share/consoles_libraries/
WORKDIR /prometheus
RUN ln -s /usr/share/prometheus/console_libraries /usr/share/prometheus/consoles/ /etc/prometheus/
EXPOSE 9090
ENTRYPOINT [ "/bin/prometheus" ]
CMD [ "--config.file=/etc/prometheus/prometheus.yml", \
      "--storage.tsdb.path=/prometheus", \
      "--web.console.libraries=/usr/share/prometheus/console_libraries", \
      "--web.console.templates=/usr/share/prometheus/consoles" ]
