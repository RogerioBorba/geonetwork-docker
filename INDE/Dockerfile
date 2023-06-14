ARG GEONETWORK_VERSION=3.10.2

FROM cmotadev/geonetwork:${GEONETWORK_VERSION}

# INDE Metadata profiles and patches
# https://inde.gov.br/Suporte/InstalacaoGN
COPY ["mgb/legado/", "mgb/2.0/", "webapps/geonetwork/WEB-INF/data/config/schema_plugins/"]
COPY patch/ webapps/geonetwork/

# Enable MGB Profiles in geonetwork
RUN mv webapps/geonetwork/WEB-INF/data/config/schema_plugins/config-spring-mgb*.xml webapps/geonetwork/WEB-INF && \
    sed -i '49i <import resource="config-spring-mgb.xml"/>\n<import resource="config-spring-mgb-2.xml"/>' \
        ./webapps/geonetwork/WEB-INF/config-spring-geonetwork.xml
