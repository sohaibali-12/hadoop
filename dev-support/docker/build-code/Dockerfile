FROM hadoop-base:v1 As buildServer

WORKDIR /usr/src/securiti/hadoop
COPY . .
RUN mvn package -Pdist -DskipTests -Dtar -Dmaven.javadoc.skip=true


FROM amazoncorretto:11
WORKDIR /usr/src/securiti
COPY --from=buildServer /usr/src/securiti/hadoop/hadoop-client-modules/hadoop-client-runtime/target/hadoop-client-runtime-3.3.6.jar hadoop-client-runtime-3.3.6.jar
