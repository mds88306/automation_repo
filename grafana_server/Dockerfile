FROM ubuntu
RUN mkdir -p /grafana
COPY test.sh /grafana/
RUN apt-get update -y 
RUN apt-get install -y apt-transport-https && apt-get install -y software-properties-common wget
RUN wget -q -O /usr/share/keyrings/grafana.key https://apt.grafana.com/gpg.key
RUN echo "deb [signed-by=/usr/share/keyrings/grafana.key] https://apt.grafana.com stable main" | tee -a /etc/apt/sources.list.d/grafana.list
RUN apt-get update -y
RUN apt-get install grafana -y
WORKDIR /grafana
RUN chmod +x test.sh
EXPOSE 3000
CMD ./test.sh
ENTRYPOINT /bin/bash
