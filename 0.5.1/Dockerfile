FROM node:13.10.1-buster

RUN mkdir -p /foundrydata/
RUN mkdir -p /root/.local/share/FoundryVTT

ENV FOUNDRY_HOME=/home/foundry/fvtt
RUN mkdir -p $FOUNDRY_HOME

RUN useradd -d "$FOUNDRY_HOME" foundry && ls -al $FOUNDRY_HOME
RUN chown foundry:foundry $FOUNDRY_HOME && chown foundry:foundry /foundrydata/

WORKDIR "${FOUNDRY_HOME}"

# installing unzip and bash shell
RUN apt-get update && \
 apt-get install -y \
		 unzip \
 && rm -rf /var/lib/apt/lists/*

USER foundry
# copy found
COPY ./foundryvtt*.zip .

# unzip 
RUN unzip foundryvtt*.zip
RUN rm foundryvtt*.zip

EXPOSE 30000
CMD [ "node", "resources/app/main.js", "--dataPath=/foundrydata/" ]
