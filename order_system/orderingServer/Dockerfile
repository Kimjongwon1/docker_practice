FROM openjdk:11 as stage1

WORKDIR /app

#gradle 빌드시에 필요한 파일들을 workdir로 copy하는 작업
COPY gradlew .
COPY gradle gradle
COPY build.gradle .
COPY settings.gradle .
COPY src src
#/app/build/libs/*.jar 파일 아래 명령어를 통해 생성
RUN ./gradlew bootJar

FROM openjdk:11

WORKDIR /app

COPY --from=stage1 /app/build/libs/*.jar app.jar

#CMD 또는 ENTRYPOINT를 통해 컨테이너 실행
ENTRYPOINT ["java","-jar","app.jar"]
