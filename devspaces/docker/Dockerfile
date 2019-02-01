FROM ubuntu:18.04

LABEL description="This file generates a docker image containing everything needed to build and run TravelMate project."

ENV DEBIAN_FRONTEND=noninteractive

RUN apt-get update && \
    apt-get install -y python3 python3-pip postgresql && \
    apt-get clean    

USER postgres
RUN service postgresql start && \
    createuser nomad && \
    createdb nomad && \
    psql -c "alter user nomad with encrypted password 'pass';" && \
    psql -c "grant all privileges on database nomad to nomad;" && \
    psql -c "ALTER USER nomad CREATEDB;"   

CMD service postgresql start && tail -f /dev/null