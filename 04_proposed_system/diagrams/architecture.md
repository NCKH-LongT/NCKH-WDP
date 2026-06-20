# System Architecture Diagram

> Placeholder — xuất file `architecture.png` từ draw.io và đặt vào thư mục này (mục tiêu: Tuần 6).

## Mô tả kiến trúc (để vẽ diagram)

```
+-----------------------------------------------------+
|                   FRONTEND LAYER                    |
|  React.js + Tailwind CSS + Ant Design (3 giao dien) |
|  [Admin Dashboard] [Contestant Portal] [Judge UI]   |
+----------------------+------------------------------+
                       | REST API (HTTPS)
+----------------------v------------------------------+
|                  BACKEND LAYER                      |
|        Node.js + Express.js (TypeScript)            |
|  [Auth API] [Competition API] [AI Proxy API]        |
+------+-----------------------------+----------------+
       |                             |
+------v------+          +-----------v-----------------+
|   MongoDB   |          |      AI SERVICE LAYER       |
|  (Mongoose) |          |   Node.js + TypeScript      |
|             |          |  [Email Generator]          |
| competitions|          |  [Question Generator]       |
| teams       |          |  [Timeline Agent/node-cron] |
| milestones  |          +-----------+----------------+
| email_drafts|                      | API Call
| question_set|          +-----------v-----------------+
+-------------+          |     EXTERNAL SERVICES       |
                         |  Gemini 1.5 Flash (Email)   |
                         |  Gemini 1.5 Pro (Questions) |
                         |  Google OAuth 2.0 (Auth)    |
                         +-----------------------------+
```

## Công cụ vẽ

- draw.io: nhập mô tả trên và xuất PNG với tên `architecture.png`
- Kích thước khuyến nghị: 1200 x 800 px
