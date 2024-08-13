FROM gradle:7 AS base

CMD ["bash"]


# build
FROM base AS build
COPY . /workspace
WORKDIR /workspace
RUN ./gradlew build

# procution
FROM openjdk:17 AS production
COPY --from=build /workspace/build/libs/api-0.0.1-SNAPSHOT.ja ./api.jar
CMD ["java", "-jar", "api.jar"]