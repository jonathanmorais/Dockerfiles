# -- build env

FROM openjdk:12 AS build

RUN mkdir -p /WORKSPACE
WORKDIR /WORKSPACE
COPY . .
RUN yum install -y wget unzip
RUN wget -O gradle-5.6.4-bin.zip https\://services.gradle.org/distributions/gradle-5.6.4-bin.zip && \
    unzip gradle-5.6.4-bin.zip -d /opt && \
    mv /opt/gradle-5.6.4 /opt/gradle

RUN /opt/gradle/bin/gradle build

# -- deploy env

FROM openjdk:12 AS deploy

RUN mkdir -p /opt/app

# change variable snapshot version
COPY --from=build /WORKSPACE/build/libs/*.jar /opt/app/*.jar

ENTRYPOINT ["java", "-jar", "/opt/app/*.jar"]
