FROM ibmcom/websphere-traditional:latest

USER root

RUN mkdir /demo && chown was /demo

USER was
RUN mkdir /demo/db2drivers
COPY Binary/db2drivers/db2jcc.jar /demo/db2drivers
COPY Binary/db2drivers/db2jcc_license_cu.jar /demo/db2drivers

COPY customCmd.properties /demo/
COPY wsadmin.py /demo/
COPY Binary/HelloWorld.war /demo/
COPY Binary/pbw-ear8.ear /demo/
###COPY pbw-ear7.ear /demo/
COPY transformationadvisor* /demo/

WORKDIR "/demo"
###RUN cat transformationadvisor-Linux_test_test.tgz > transformationadvisor-2.1_Linux_Demo1.tgz
###RUN tar xvfz transformationadvisor-2.1_Linux_Demo1.tgz
###COPY customCmd.properties /demo/transformationAdvisor*/conf/
### USE NEWER COLLECTOR

RUN tar xvfz transformationadvisor-Linux_Demo_Demo.tgz
<<<<<<< HEAD
#COPY customCmd.properties /demo/transformationadvisor-2.1.1/conf/
=======
# COPY customCmd.properties /demo/transformationadvisor-2.1.1/conf/
>>>>>>> cbace62d97a93861c2d60eea5beb187c2ad70b04


COPY PASSWORD /tmp/PASSWORD
ENV pwd=passw0rd
RUN echo $pwd

RUN wsadmin.sh -lang jython -f /demo/wsadmin.py -conntype NONE -username wsadmin -password passw0rd

