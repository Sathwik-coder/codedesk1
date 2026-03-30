# CodeDesk ✦

A fast, minimal, live code editor with instant sharing — like CodePen but cleaner.

Built with **React + Vite + Monaco Editor** (frontend) and **Node.js + Express + MongoDB** (backend).

---

## ✦ Features

- **Monaco Editor** (VS Code engine) with a custom dark theme
- **HTML / CSS / JS** tabs — live preview via `srcDoc` iframe
- **Auto-run** with debounce (600ms after last keystroke)
- **Ctrl+Enter** keyboard shortcut to run
- **Share** — saves pad to DB, generates a short URL, copies to clipboard
- **Auto-save** — debounced 1.2s after changes on a shared pad
- **Download** — exports a self-contained `.html` file
- **Console panel** — captures `console.log/warn/error` from the iframe
- **Resizable split pane** — drag the divider
- **Fullscreen editor** mode
- **Reset** to starter defaults

---

## 📁 Folder Structure

```
codedesk/
├── frontend/               # React + Vite app
│   ├── src/
│   │   ├── components/
│   │   │   ├── TopBar.jsx
│   │   │   ├── CodeEditor.jsx
│   │   │   ├── Preview.jsx
│   │   │   ├── Resizer.jsx
│   │   │   └── Toast.jsx
│   │   ├── hooks/
│   │   │   ├── usePad.js
│   │   │   └── useDebounce.js
│   │   ├── pages/
│   │   │   └── EditorPage.jsx
│   │   ├── utils/
│   │   │   └── api.js
│   │   ├── App.jsx
│   │   ├── main.jsx
│   │   └── index.css
│   ├── index.html
│   ├── vite.config.js
│   ├── tailwind.config.js
│   ├── postcss.config.js
│   ├── .env.example
│   └── package.json
│
└── backend/                # Node.js + Express API
    ├── src/
    │   ├── models/
    │   │   └── Pad.js
    │   ├── routes/
    │   │   └── pad.js
    │   └── index.js
    ├── .env.example
    └── package.json
```

---

## 🚀 Local Setup

### 1. Clone the repo

```bash
git clone https://github.com/yourname/codedesk.git
cd codedesk
```

### 2. Backend setup

```bash
cd backend
npm install
cp .env.example .env
# Edit .env with your MongoDB URI
npm run dev
# → API running on http://localhost:4000
```

**`.env` file:**
```
PORT=4000
MONGODB_URI=mongodb+srv://<user>:<pass>@cluster.mongodb.net/codedesk
FRONTEND_URL=http://localhost:5173
```

> You can use a free [MongoDB Atlas](https://www.mongodb.com/atlas) cluster.

### 3. Frontend setup

```bash
cd frontend
npm install
cp .env.example .env
# .env already has VITE_API_URL=http://localhost:4000
npm run dev
# → App running on http://localhost:5173
```

---

## 🌐 API Reference

| Method | Endpoint    | Body              | Description       |
|--------|-------------|-------------------|-------------------|
| POST   | /pad        | {html, css, js}   | Create a new pad  |
| GET    | /pad/:id    | —                 | Load a pad by ID  |
| PUT    | /pad/:id    | {html, css, js}   | Update a pad      |

---

## ☁️ Deployment

### Frontend → Vercel

1. Push `frontend/` to GitHub
2. Import in [Vercel](https://vercel.com)
3. Set environment variable:
   ```
   VITE_API_URL=https://your-backend.onrender.com
   ```
4. Deploy — Vercel auto-detects Vite

### Backend → Render

1. Push `backend/` to GitHub
2. Create a new **Web Service** on [Render](https://render.com)
3. Set:
   - **Build Command:** `npm install`
   - **Start Command:** `npm start`
4. Add environment variables:
   ```
   MONGODB_URI=mongodb+srv://...
   FRONTEND_URL=https://your-app.vercel.app
   PORT=4000
   ```

---

## 🎨 Tech Stack

| Layer     | Tech                              |
|-----------|-----------------------------------|
| Frontend  | React 18, Vite, Tailwind CSS      |
| Editor    | Monaco Editor (`@monaco-editor/react`) |
| Routing   | React Router v6                   |
| HTTP      | Axios                             |
| Backend   | Node.js, Express.js               |
| Database  | MongoDB + Mongoose                |
| ID gen    | nanoid (8-char short IDs)         |

---

## 📝 License

MIT
