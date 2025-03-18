# Outline 
1. Chạy ứng dụng không cần dùng Docker
2. Chạy ứng dụng với Docker
3. Chạy ứng dụng K8s
# Chạy ứng dụng không cần dùng Docker
##### Buid 
``` ./mvnw package ```
##### Chạy file jar
``` java -jar target/spring-boot-docker-complete-0.0.1-SNAPSHOT.jar ```
##### Truy cập 
- Truy cập ứng dụng trên ```localhost:8080``` hiển thị ứng dụnng.
![image](https://github.com/user-attachments/assets/bc2ef97d-85df-45c0-af17-d9d5f516b57a)


# Chạy dự án sử dụng Docker 
### Containerize ứng dụng (Build Docker Image)
- Chạy lệnh build docker
``` docker build -t springio/gs-spring-boot-docker . ```
![image](https://github.com/user-attachments/assets/a32b4564-1435-4273-84d2-ae4e1d0a8c61)

### Chạy container
``` docker run -p 8080:8080 springio/gs-spring-boot-docker ```
![image](https://github.com/user-attachments/assets/5ffdbaa8-3dbd-423c-a369-3d4b548b95ca)

###### Container đã đang chạy trong docker:
![image](https://github.com/user-attachments/assets/758a4436-9f12-409d-8f7b-f48bec0034ff)

###### Lệnh ` -p 8080:8080 `: Ánh xạ cổng 8080 từ container ra host
###### Mở trình duyệt tại ``` http://localhost:8080 ```
![image](https://github.com/user-attachments/assets/d59ffe0a-1b4d-45e5-98a2-5f5479ebec24)

# Chạy ứng dụng với K8s 
### Tạo Docker Image
Chuyển vào thư mục `hello-spring-k8s` và tạo image bằng Cloud Native Buildpacks
```cd hello-spring-k8s```
```./mvnw spring-boot:build-image -Dspring-boot.build-image.imageName=spring-k8s/hello-spring-k8s ```
###### Kiểm tra Image
Sử dụng lệnh ``` docker images spring-k8s/hello-spring-k8s ``` để kiểm tra ouput. Output hiển thị như dưới đây sẽ thể hiện build image thành công

![image](https://github.com/user-attachments/assets/4277f229-3de3-4302-a1d0-e7a19a471559)

### Chạy kiểm tra container 
```docker run -p 8080:8080 --name hello-spring-k8s -t spring-k8s/hello-spring-k8s```
![image](https://github.com/user-attachments/assets/5eb73f2f-c8bf-4e6f-8b18-264d2da8ab01)
![image](https://github.com/user-attachments/assets/f09caef9-fe20-483b-ba75-f1d767fd07d3)

##### Tắt container sau khi kiểm tra 
``` docker stop hello-spring-k8s ```

### Triển khai lên K8s
##### Khởi tạo YAML 
``` mkdir k8s ```
``` cd k8s ``` 
- Tạo file `deployment.yaml` và `service.yaml`
- Chuyển tiếp cổng để truy cập service
  ``` kubectl port-forward svc/gs-spring-boot-k8s 9090:80 ```
- Kiểm tra trên localhost
  ![image](https://github.com/user-attachments/assets/f3658158-bdd2-4217-9692-a4c66b7ca2f3)
- Kiểm tra trên terminal
  ![image](https://github.com/user-attachments/assets/25607a4e-0591-422c-91de-fd70a93d361c)
- Trên giao diện docker
  ![image](https://github.com/user-attachments/assets/222a0968-5a5e-42ab-8e45-f41d14012f50)


