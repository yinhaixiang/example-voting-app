FROM java:7

RUN wget http://apache-mirror.rbc.ru/pub/apache/maven/maven-3/3.3.9/binaries/apache-maven-3.3.9-bin.tar.gz
RUN tar xzvf apache-maven-3.3.9-bin.tar.gz
RUN cp -R apache-maven-3.3.9 /usr/local/bin
RUN export PATH=/usr/local/bin/apache-maven-3.3.9/bin:$PATH
RUN ln -s /usr/local/bin/apache-maven-3.3.9/bin/mvn /usr/local/bin/mvn

RUN mkdir /var/tmp/webapp
ADD src /var/tmp/webapp
ADD pom.xml /var/tmp/webapp
ADD settings.xml /var/tmp/webapp
RUN cd /var/tmp/webapp && mvn package --settings settings.xml
CMD ["/usr/lib/jvm/java-7-openjdk-amd64/bin/java", "-jar", "target/worker-jar-with-dependencies.jar"]