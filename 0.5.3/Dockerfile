FROM node:13.10.1-alpine3.10

RUN mkdir -p /root/.local/share/FoundryVTT
RUN mkdir -p /foundrydata/

ENV FOUNDRY_HOME=/home/foundry/fvtt
RUN mkdir -p $FOUNDRY_HOME

# create the foundry use
RUN adduser --disabled-password --uid 1001 --home "$FOUNDRY_HOME" foundry && ls -al $FOUNDRY_HOME

RUN chown foundry:foundry $FOUNDRY_HOME && chown foundry:foundry /foundrydata/ && ls -al $FOUNDRY_HOME/..

WORKDIR "${FOUNDRY_HOME}"

RUN apk add curl unzip

USER foundry
COPY ./foundryvtt*.zip .

RUN unzip foundryvtt*.zip
RUN rm foundryvtt*.zip

EXPOSE 30000
CMD [ "node", "resources/app/main.js", "--dataPath=/foundrydata/" ]
