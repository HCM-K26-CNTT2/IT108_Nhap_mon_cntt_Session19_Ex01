## Chỉ ra tại sao tệp .env vẫn bị đẩy lên GitHub.
- `.gitignore` chỉ có `node_modules/` và `dist/`, **thiếu dòng `.env`** nên Git coi nó là tệp bình thường. Khi chạy `git add .`, tệp `.env` bị đưa vào commit và push lên GitHub.
- Nếu `.env` đã từng được commit trước đó, thêm vào `.gitignore` sau này **không có tác dụng**, vì `.gitignore` chỉ áp dụng cho tệp chưa được theo dõi (untracked).
## Cung cấp nội dung tệp .gitignore đã được sửa đúng
```gitignore
node_modules/
dist/

# Biến môi trường (chứa khóa bí mật)
.env
.env.*
!.env.example
```

- `.env` và `.env.*`: chặn tệp chính và các biến thể (`.env.local`, `.env.production`...).
- `!.env.example`: ngoại lệ, cho phép đẩy tệp mẫu chỉ chứa tên biến, **không có giá trị thật**.

Ví dụ `.env.example`:

```env
OPENAI_API_KEY=your_key_here
```
## Giải thích cơ chế ẩn thông tin trên VS Code.
- VS code sẽ tự động chuyển màu tệp .env sang dạng xám mờ để bảo hiệu tệp đã được bảo vệ an toàn.
