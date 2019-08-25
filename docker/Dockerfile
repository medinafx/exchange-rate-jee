FROM jboss/wildfly:17.0.1.Final

ARG user="admin"
ARG pass="admin"

COPY --chown=jboss:jboss docker/files/module.xml /opt/jboss/wildfly/modules/system/layers/base/org/postgresql/main/module.xml
COPY --chown=jboss:jboss docker/lib/postgresql-42.2.6.jar /opt/jboss/wildfly/modules/system/layers/base/org/postgresql/main/postgresql-42.2.6.jar
COPY --chown=jboss:jboss docker/files/standalone.xml /opt/jboss/wildfly/standalone/configuration/standalone.xml
COPY --chown=jboss:jboss target/exchange-rate-jee.war /opt/jboss/wildfly/standalone/deployments

RUN /opt/jboss/wildfly/bin/add-user.sh $user $pass --silent

ENTRYPOINT ["/opt/jboss/wildfly/bin/standalone.sh"]
CMD ["-b", "0.0.0.0", "-bmanagement", "0.0.0.0"]