Báo cáo Phân tích Lý thuyết về Path Traversal và File Upload Vulnerability

1. Path Traversal Vulnerability

Mô tả

Path Traversal (Directory Traversal) là một lỗ hổng bảo mật cho phép kẻ tấn công truy cập vào các tệp hoặc thư mục nằm ngoài thư mục gốc dự kiến của ứng dụng web. Lỗ hổng này thường xảy ra khi ứng dụng xử lý không đúng cách các tham số đầu vào từ phía người dùng, đặc biệt là tên tệp hoặc đường dẫn tệp.

Cơ chế khai thác

Kẻ tấn công lợi dụng các ký tự đặc biệt như ../ hoặc ..\ để điều hướng đến thư mục cha, từ đó truy xuất các tập tin nhạy cảm như:

../../../../etc/passwd (Unix/Linux)

..\..\..\windows\win.ini (Windows)

Ví dụ:

URL dễ bị tấn công:

http://example.com/download?file=report.pdf

Kẻ tấn công thay đổi giá trị:

http://example.com/download?file=../../../../etc/passwd

Nếu ứng dụng không kiểm tra kỹ đầu vào, nó sẽ trả về nội dung file /etc/passwd.

Demo:

Tiến hành kiểm thử mục tiêu
<img width="915" height="401" alt="image" src="https://github.com/user-attachments/assets/42bc5f51-5041-46ef-8326-9e1a3e0be19d" />
