# FROM openjdk:17-jdk-slim
FROM gradle:8.8-jdk17-alpine

# WORKDIR /app

# # dos2unix 유틸리티 설치 (apt-get update와 함께 실행)
# # 이 유틸리티는 Windows 스타일의 줄 바꿈(CRLF)을 Unix 스타일(LF)로 변환합니다.
# RUN apt-get update && apt-get install -y dos2unix && rm -rf /var/lib/apt/lists/*

# # Gradle Wrapper 파일 복사
# COPY gradlew .
# COPY gradle ./gradle

# # gradlew 파일의 줄 바꿈 문자를 LF로 변환
# RUN dos2unix gradlew

# RUN chmod +x gradlew

# # 빌드 설정 파일 복사
# COPY build.gradle .
# COPY settings.gradle .

# # 의존성 미리 다운로드
# # RUN ./gradlew build --no-daemon --parallel --continue --stacktrace -x test || true

# # 전체 소스 코드 복사 (실제 실행 시에는 볼륨으로 대체)
# COPY . .
# # RUN chmod +x ./gradlew

# # 개발 환경에서는 디버깅 포트를 열어둡니다.
# EXPOSE 8080

# # 애플리케이션을 devtools 모드로 실행
# CMD ["./gradlew", "bootRun"]

WORKDIR /app
COPY . .
RUN gradle bootJar
RUN chmod +x build/libs/todo-v1-0.0.1-SNAPSHOT.jar
EXPOSE 8080
CMD ["java", "-jar", "build/libs/todo-v1-0.0.1-SNAPSHOT.jar"]
