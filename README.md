# Bài tập: Bảo vệ API Key bằng .gitignore

## 1. Nguyên nhân

`.gitignore` chỉ chứa `node_modules/` và `dist/`, chưa loại trừ `.env`, nên Git có thể đưa file chứa `OPENAI_API_KEY` lên GitHub.

## 2. Sửa `.gitignore`

```gitignore
node_modules/
dist/
.env
.env.*
!.env.example
```

Nếu `.env` đã được Git theo dõi:

```bash
git rm --cached .env
git commit -m "Remove .env from Git"
git push
```

**Quan trọng:** Thu hồi API Key đã lộ, tạo khóa mới. Các lệnh trên không xóa khóa khỏi lịch sử commit cũ.

## 3. Cơ chế trong VS Code

- `.gitignore` ngăn Git theo dõi file chưa được theo dõi; không mã hóa hay ẩn file trong VS Code.
- `.env` vẫn nằm trên máy để ứng dụng sử dụng.
- `files.exclude` chỉ ẩn file khỏi Explorer của VS Code, không bảo mật dữ liệu.

**Kết luận:** Loại trừ `.env` trước khi commit và không đưa khóa API thật lên GitHub.
