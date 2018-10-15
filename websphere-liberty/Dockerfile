# FROM websphere-liberty:webProfile7
# FROM 172.30.1.1:5000/openshift/websphere-liberty:webProfile7
FROM 172.30.1.1:5000/myproject/wlp-centos:dudo

# Add binary deployment artifact to 'dropins' folder
# RUN wget --directory-prefix=/opt/ibm/wlp/usr/servers/defaultServer/dropins/ $BINARY_DEPLOYMENT_ARTIFACT_URL
# COPY jvm.options /config/jvm.options
COPY usr/ /opt/ibm/wlp/usr/
COPY app/* /opt/ibm/wlp/usr/servers/defaultServer/dropins/

# RUN chmod a+rwx /opt/ibm/wlp/output/defaultServer
# RUN chmod 777 -R /opt/ibm/wlp/ /logs
RUN useradd -u 1001 -r -g 0 -s /sbin/nologin default \
    && chown -R 1001:0 /config \
    && chmod -R g+rw /config \
    && chown -R 1001:0 /opt/ibm/docker/docker-server \
    && chmod -R g+rwx /opt/ibm/docker/docker-server \
    && chown -R 1001:0 /opt/ibm/wlp/usr/servers/defaultServer \
    && chmod -R g+rw /opt/ibm/wlp/usr/servers/defaultServer \
    && chown -R 1001:0 /opt/ibm/wlp/output \
    && chmod -R g+rw /opt/ibm/wlp/output \
    && chown -R 1001:0 /logs \
    && chmod -R g+rw /logs

# IBM WebSphere Liberty license must be accepted
ENV LICENSE $LICENSE

USER 1001

