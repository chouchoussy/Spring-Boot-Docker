# Sử dụng image cơ sở OpenJDK 17
FROM openjdk:17-jdk-slim

# Đặt thư mục làm việc
WORKDIR /app

# Sao chép tệp pom.xml và các tệp cần thiết để tải dependencies
COPY pom.xml ./
COPY .mvn .mvn
COPY mvnw ./
COPY mvnw.cmd ./

# Tải dependencies
RUN ./mvnw dependency:go-offline -B

# Sao chép toàn bộ mã nguồn
COPY src ./src

# Build ứng dụng
RUN ./mvnw package -DskipTests

# Sao chép file JAR đã build vào image
COPY target/*.jar app.jar

# Mở cổng 8080 (mặc định của Spring Boot)
EXPOSE 8080

# Lệnh chạy ứng dụng
ENTRYPOINT ["java", "-jar", "app.jar"]