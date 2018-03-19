FROM dingwenxiang0/alpine-glibc:3.7

MAINTAINER saruman 624380857@qq.com

ARG JAVA_VERSION=8
ARG JAVA_UPDATE=162
ARG JAVA_BUILD=12
ARG JAVA_PATH=0da788060d494f5095bf8624735fa2f1
ARG JAVA_FULL_VERSION=${JAVA_VERSION}u${JAVA_UPDATE}
ARG JAVA_FULL_VERSION_BUILD=${JAVA_FULL_VERSION}-b${JAVA_BUILD}
ARG JAVA_DOWNLOAD_URL=http://download.oracle.com/otn-pub/java/jdk/${JAVA_FULL_VERSION_BUILD}/${JAVA_PATH}/jre-${JAVA_FULL_VERSION}-linux-x64.tar.gz
ARG JAVA_JCE_DOWNLOAD_URL=http://download.oracle.com/otn-pub/java/jce/${JAVA_VERSION}/jce_policy-${JAVA_VERSION}.zip

ENV JAVA_HOME=/app/tools/java/jre
ENV PATH=${PATH}:${JAVA_HOME}/bin
ENV CLASSPATH=.:${JAVA_HOME}/lib:${CLASSPATH}

RUN apk add --no-cache --virtual=build-dependencies wget ca-certificates unzip \
    && mkdir -p /app/tools/java \
    && cd /app/tools/java \
    && wget --header "Cookie: oraclelicense=accept-securebackup-cookie" "${JAVA_DOWNLOAD_URL}" \
    && tar -zxf jre-${JAVA_FULL_VERSION}-linux-x64.tar.gz \
    && ln -s /app/tools/java/jre1.${JAVA_VERSION}.0_${JAVA_UPDATE} /app/tools/java/jre \
    && wget --header "Cookie: oraclelicense=accept-securebackup-cookie;" "${JAVA_JCE_DOWNLOAD_URL}" \
    && unzip -jo -d "${JAVA_HOME}/lib/security" "jce_policy-${JAVA_VERSION}.zip" \
    && apk del build-dependencies \
    && rm -rf jre-8u162-linux-x64.tar.gz \
    && rm -rf jce_policy-${JAVA_VERSION}.zip