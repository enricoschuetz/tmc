FROM alpine:latest

# externally configurable environment variables
# either set default here or set with docker run option -e
ENV TMC_URLCONTEXTROOT=
ENV TMC_LOGLEVEL=INFO
ENV TMC_CORSALLOWEDORIGINS=
ENV TMC_CORSALLOWEDHEADERS=
ENV TMC_CORSALLOWCREDENTIALS=
ENV TMC_CORSMAXAGE=86500

      
ENV WORKDIR /thingmodels

RUN apk update \
 && apk add --no-cache curl jq \
 && rm -rf /var/cache/apk/*

WORKDIR $WORKDIR 

# fetch the latest tmc for linux
COPY ./docker/download-cli.sh .
RUN ./download-cli.sh; rm ./download-cli.sh
RUN chmod 755 ./tmc-clone; mv ./tmc-clone /usr/bin;


ENTRYPOINT ["tmc-clone"]
