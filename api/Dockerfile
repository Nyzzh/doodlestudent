FROM alpine:3.17 AS build
RUN apk add --no-cache maven git
RUN git clone https://github.com/Nyzzh/doodlestudent.git
WORKDIR /doodlestudent/api
RUN git checkout develop
RUN mvn clean package -Dquarkus.package.type=uber-jar

FROM alpine:3.17
RUN apk add --no-cache openjdk11
COPY --from=build /doodlestudent/api/target/tlcdemoApp-1.0.0-SNAPSHOT-runner.jar /target/
CMD [ "java", "-jar", "/target/tlcdemoApp-1.0.0-SNAPSHOT-runner.jar" ]