# Chạy ứng dụng không cần dùng Docker
#### Buid 
``` ./mvnw package ```
#### Chạy file jar
``` java -jar target/spring-boot-docker-complete-0.0.1-SNAPSHOT.jar ```
#### Truy cập 
- Truy cập ứng dụng trên ```localhost:8080``` hiển thị ứng dụnng.
- ![image](https://github.com/user-attachments/assets/bc2ef97d-85df-45c0-af17-d9d5f516b57a)

# Chạy dự án sử dụng Docker 
## Containerize ứng dụng (Build Docker Image)
- Chạy lệnh build docker
``` docker build -t springio/gs-spring-boot-docker . ```
![image](https://github.com/user-attachments/assets/a32b4564-1435-4273-84d2-ae4e1d0a8c61)

## Chạy container
``` docker run -p 8080:8080 springio/gs-spring-boot-docker ```
![image](https://github.com/user-attachments/assets/5ffdbaa8-3dbd-423c-a369-3d4b548b95ca)

- Container đã đang chạy trong docker:
![image](https://github.com/user-attachments/assets/758a4436-9f12-409d-8f7b-f48bec0034ff)

- Lệnh ` -p 8080:8080 `: Ánh xạ cổng 8080 từ container ra host
- Mở trình duyệt tại ``` http://localhost:8080 ```
  ![image](https://github.com/user-attachments/assets/d59ffe0a-1b4d-45e5-98a2-5f5479ebec24)
