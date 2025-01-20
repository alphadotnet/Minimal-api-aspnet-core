# TodoAPI với ASP.NET Core Minimal API

## Tổng quan
Đây là một ứng dụng API đơn giản được xây dựng bằng ASP.NET Core Minimal API để quản lý danh sách công việc (Todo List). Ứng dụng sử dụng Entity Framework Core với cơ sở dữ liệu InMemory để lưu trữ dữ liệu.

## Các tính năng chính

### Quản lý công việc (Todo Items)
* Xem tất cả công việc
* Xem các công việc đã hoàn thành
* Xem chi tiết một công việc
* Tạo công việc mới
* Cập nhật công việc
* Xóa công việc

### Swagger UI Integration
* Tích hợp Swagger UI để dễ dàng test API
* Documentation tự động cho các endpoints
* Giao diện trực quan để thử nghiệm API

## Cấu trúc dữ liệu

### Todo Item
* **Id**: Định danh unique của công việc
* **Name**: Tên công việc
* **IsComplete**: Trạng thái hoàn thành
* **Secret**: Thông tin bảo mật (chỉ lưu trong DB)

## Công nghệ sử dụng

### MapGroup
MapGroup là tính năng cho phép nhóm các endpoints API có chung prefix URL. Giúp tổ chức code tốt hơn, giảm code trùng lặp và dễ dàng áp dụng middleware cho nhóm endpoints.

### TypedResults
TypedResults cung cấp các phương thức trả về strongly-typed results, đảm bảo type safety và tối ưu hiệu suất. Hỗ trợ IntelliSense tốt và làm code rõ ràng, dễ đọc hơn.

## API Endpoints

| Method | Endpoint | Mô tả |
|--------|----------|--------|
| GET | /todoitems | Lấy danh sách tất cả công việc |
| GET | /todoitems/complete | Lấy danh sách công việc đã hoàn thành |
| GET | /todoitems/{id} | Lấy chi tiết một công việc |
| POST | /todoitems | Tạo công việc mới |
| PUT | /todoitems/{id} | Cập nhật một công việc |
| DELETE | /todoitems/{id} | Xóa một công việc |

## Hướng dẫn sử dụng

### Khởi động ứng dụng
1. Chạy ứng dụng trong môi trường Development
2. Truy cập Swagger UI tại đường dẫn: `/swagger`

### Sử dụng API
* Tất cả request/response đều ở dạng JSON
* Sử dụng Swagger UI để test các endpoints
* Có thể sử dụng các công cụ như Postman để test API

## Kết quả demo

### 1. Swagger UI interface
![Image](https://github.com/user-attachments/assets/7d6274d9-ffb6-4c75-a805-9d06164021f1)

### 2. POST /todoitems 
```json
{
  "name":"walk dog",
  "isComplete":true
}
```
![Image](https://github.com/user-attachments/assets/97d5d976-3e4a-4f53-ad08-6e4d1bcc55c0)

### 3. GET /todoitems 
![Image](https://github.com/user-attachments/assets/1b1fb533-2797-4236-a8a2-70f4b95b8ed7)

### 4. GET /todoitems/{id} 
![Image](https://github.com/user-attachments/assets/cede9603-fe8e-40b5-b40c-ceeb0e5eef8a)

### 5. GET /todoitems/complete
![Image](https://github.com/user-attachments/assets/0c0f1cb1-8b25-4720-a965-ec66278107f3)

### 6. PUT /todoitems/{id}
* Đặt nội dung yêu cầu thành JSON sau:
```json
{
  "name": "feed fish",
  "isComplete": false
}
```
![Image](https://github.com/user-attachments/assets/59081027-8f62-4f22-82ed-d554b46fbf4a)
* Sau khi PUT ta xem lại dữ liệu bằng GET /todoitems
![Image](https://github.com/user-attachments/assets/1037fef7-5fa5-4137-b7b0-be1f7dc478c8)

### 7. DELETE /todoitems/{id}
![Image](https://github.com/user-attachments/assets/a73221d3-9757-4950-a3a3-e84d2ddde9e1)
* Sau khi DELETE ta xem lại dữ liệu bằng GET /todoitems
![Image](https://github.com/user-attachments/assets/270045d7-d4d8-4c6a-92a7-116497059707)
  
## Lưu ý bảo mật

* Sử dụng DTO pattern để tránh lộ thông tin nhạy cảm
* Field `Secret` trong model `Todo` không được expose qua API
* Swagger UI chỉ được bật trong môi trường Development

## Ưu điểm của Minimal API

1. Code ngắn gọn, dễ đọc
2. Ít boilerplate code
3. Hiệu năng tốt
4. Dễ dàng setup và maintain
5. Phù hợp cho các ứng dụng nhỏ và microservices

## Kết luận

Đây là một ví dụ tốt về cách xây dựng REST API đơn giản với ASP.NET Core Minimal API. Code được tổ chức tốt, có tính bảo mật và dễ dàng mở rộng trong tương lai.

## Tham khảo
Bài làm được tham khảo bởi https://learn.microsoft.com/en-us/aspnet/core/tutorials/min-web-api?view=aspnetcore-9.0&tabs=visual-studio-code
