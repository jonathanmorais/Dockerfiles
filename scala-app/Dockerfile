# first stage - build
ARG OPENJDK_TAG=8u212-stretch

FROM openjdk:${OPENJDK_TAG} AS build

ARG SBT_VERSION=1.2.8

# Install sbt
RUN \
  curl -L -o sbt-$SBT_VERSION.deb https://dl.bintray.com/sbt/debian/sbt-$SBT_VERSION.deb && \
  dpkg -i sbt-$SBT_VERSION.deb && \
  rm sbt-$SBT_VERSION.deb && \
  apt-get update && \
  apt-get install sbt && \
  sbt sbtVersion

WORKDIR /usr/app/Main

ADD . /usr/app/Main


# second stage - run
FROM openjdk:8u212-b04-jre-slim-stretch

ARG MODULE_NAME

RUN mkdir /app

#ADD ./app/$MODULE_NAME/target/pack /app

RUN cd /app

COPY --from=build /usr/app/ /app/bin

CMD /app/bin/Main