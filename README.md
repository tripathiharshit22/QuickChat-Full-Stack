# 💬 QuickChat

A full-stack, real-time chat application built with the MERN stack and Socket.io. QuickChat supports instant messaging, online presence indicators, image sharing, and profile customization — all delivered through a clean, responsive UI.

---

## 🚀 Features

- 🔐 **JWT Authentication** — Secure signup, login, and persistent sessions
- ⚡ **Real-Time Messaging** — Instant bidirectional communication via Socket.io
- 🟢 **Online Presence** — Live online/offline indicators for all users
- 🖼️ **Image Sharing** — Send images in chat, uploaded via Cloudinary
- 👤 **Profile Management** — Update profile picture and display name
- ✅ **Message Seen Status** — Know when your message has been read
- 📱 **Responsive Design** — Works seamlessly on desktop and mobile

---

## 🛠️ Tech Stack

### Frontend
| Technology | Purpose |
|---|---|
| React 19 | UI framework |
| Vite 6 | Build tool & dev server |
| Tailwind CSS 4 | Utility-first styling |
| React Router DOM 7 | Client-side routing |
| Socket.io Client | Real-time communication |
| Axios | HTTP requests |
| React Hot Toast | Notifications |

### Backend
| Technology | Purpose |
|---|---|
| Node.js + Express 5 | REST API server |
| Socket.io | WebSocket server |
| MongoDB + Mongoose | Database & ODM |
| bcryptjs | Password hashing |
| JSON Web Tokens | Authentication |
| Cloudinary | Image storage & delivery |
| dotenv | Environment config |

---

## 📁 Project Structure

```
QUICKCHAT/
├── client/                   # React frontend (Vite)
│   ├── src/
│   │   ├── context/          # React context (Auth, Socket, Chat)
│   │   └── ...               # Pages, components, hooks
│   ├── .env                  # Frontend environment variables
│   └── vite.config.js
│
├── server/                   # Express backend
│   ├── controllers/          # Route handler logic
│   │   ├── userController.js
│   │   └── messageController.js
│   ├── lib/
│   │   ├── db.js             # MongoDB connection
│   │   ├── cloudinary.js     # Cloudinary config
│   │   └── utils.js          # JWT & helpers
│   ├── middleware/
│   │   └── auth.js           # JWT protect middleware
│   ├── models/
│   │   ├── User.js
│   │   └── Message.js
│   ├── routes/
│   │   ├── userRoutes.js
│   │   └── messageRoutes.js
│   ├── .env                  # Backend environment variables
│   └── server.js             # Entry point
│
└── .gitignore
```

---

## 🔌 API Reference

### Auth — `/api/auth`

| Method | Endpoint | Auth | Description |
|---|---|---|---|
| `POST` | `/signup` | ❌ | Register a new user |
| `POST` | `/login` | ❌ | Login and receive JWT |
| `PUT` | `/update-profile` | ✅ | Update profile picture |
| `GET` | `/check` | ✅ | Verify current session |

### Messages — `/api/messages`

| Method | Endpoint | Auth | Description |
|---|---|---|---|
| `GET` | `/users` | ✅ | Get all users for sidebar |
| `GET` | `/:id` | ✅ | Get conversation with a user |
| `POST` | `/send/:id` | ✅ | Send message to a user |
| `PUT` | `/mark/:id` | ✅ | Mark a message as seen |

### WebSocket Events — Socket.io

| Event | Direction | Description |
|---|---|---|
| `connection` | Client → Server | User connects with `userId` query param |
| `getOnlineUsers` | Server → All Clients | Broadcasts array of online user IDs |
| `disconnect` | Client → Server | User goes offline, presence updated |
| `newMessage` | Server → Client | Delivers message to recipient in real-time |

---

## ⚙️ Local Setup

### Prerequisites

- [Node.js](https://nodejs.org/) v18+
- [MongoDB Atlas](https://www.mongodb.com/atlas) account (or local MongoDB)
- [Cloudinary](https://cloudinary.com/) account

### 1. Clone the Repository

```bash
git clone https://github.com/your-username/quickchat.git
cd quickchat
```

### 2. Configure Environment Variables

**Server** — create `server/.env`:

```env
PORT=5000
MONGODB_URI=mongodb+srv://<username>:<password>@cluster0.xxxxx.mongodb.net/
JWT_SECRET=your_super_secret_key

CLOUDINARY_CLOUD_NAME=your_cloud_name
CLOUDINARY_API_KEY=your_api_key
CLOUDINARY_API_SECRET=your_api_secret
```

**Client** — create `client/.env`:

```env
VITE_BACKEND_URL=http://localhost:5000
```

### 3. Install Dependencies

```bash
# Server
cd server
npm install

# Client
cd ../client
npm install
```

### 4. Run the Application

```bash
# Terminal 1 — Start backend (from /server)
npm run server

# Terminal 2 — Start frontend (from /client)
npm run dev

---

## 🌐 Deployment

### Backend (e.g. Render / Railway / Vercel Serverless)

Set the following environment variables on your hosting platform:

```
PORT
MONGODB_URI
JWT_SECRET
CLOUDINARY_CLOUD_NAME
CLOUDINARY_API_KEY
CLOUDINARY_API_SECRET
NODE_ENV=production
```

The server exports a default `server` instance compatible with Vercel serverless functions.

### Frontend (e.g. Vercel / Netlify)

Set the following environment variable:

```

Run `npm run build` in the `client/` directory. Deploy the generated `dist/` folder.

---

## 🔒 Security Notes

- Passwords are hashed using **bcryptjs** before being stored
- All protected routes require a valid **JWT** passed via HTTP-only cookie or Authorization header
- The `.env` files are excluded from version control via `.gitignore`
- Never commit secrets — use environment variable management on your hosting platform

---

## 📄 License

This project is licensed under the [ISC License](https://opensource.org/licenses/ISC).

---

> Built with ❤️ using the MERN stack + Socket.io
