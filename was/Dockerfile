FROM maven:3.9-eclipse-temurin-17 AS yjmulti
WORKDIR /app

COPY was/petclinic_btc/ ./petclinic_btc

RUN echo "======== /app 디렉토리 목록 ========" && \
    ls -al /app && \
    echo "======== petclinic_btc 디렉토리 목록 ========" && \
    ls -al /app/petclinic_btc

RUN mvn -f petclinic_btc/pom.xml clean package -DskipTests -PMySQL

FROM tomcat:9.0.105-jdk11

RUN apt update && \
    apt install -y bash mysql-client && \
    rm -rf /var/lib/apt/lists/*

RUN rm -rf /usr/local/tomcat/webapps/*

COPY --from=yjmulti /app/petclinic_btc/target/petclinic.war /usr/local/tomcat/webapps/ROOT.war
