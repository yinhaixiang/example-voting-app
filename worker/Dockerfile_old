FROM java:7

RUN sed -i 's#http://archive.ubuntu.com/#http://cn.archive.ubuntu.com/#' /etc/apt/sources.list;
RUN rm -rf /var/lib/apt/lists/*
RUN mkdir /var/lib/apt/lists/partial
RUN apt-get clean
RUN apt-get update --fix-missing
RUN apt-get install -y maven && apt-get clean

WORKDIR /code

ADD pom.xml /code/pom.xml
ADD src /code/src

ADD settings.xml /code/
RUN mvn package --settings settings.xml 

CMD ["/usr/lib/jvm/java-7-openjdk-amd64/bin/java", "-jar", "target/worker-jar-with-dependencies.jar"]
