# 💬 Realtime Chat App

A modern, full-stack real-time chat application built with React, Node.js, Express, and Socket.io. Features user authentication, instant messaging, online status, and a beautiful UI with theme customization.

![React](https://img.shields.io/badge/React-19.2.0-blue?logo=react)
![Node.js](https://img.shields.io/badge/Node.js-Express-green?logo=node.js)
![Socket.io](https://img.shields.io/badge/Socket.io-4.8.3-black?logo=socket.io)
![MongoDB](https://img.shields.io/badge/MongoDB-Mongoose-green?logo=mongodb)
![Tailwind CSS](https://img.shields.io/badge/TailwindCSS-4.2.1-38B2AC?logo=tailwind-css)

## 📋 Table of Contents

- [Features](#features)
- [Tech Stack](#tech-stack)
- [Project Structure](#project-structure)
- [Prerequisites](#prerequisites)
- [Installation](#installation)
- [Configuration](#configuration)
- [Running the Application](#running-the-application)
- [API Routes](#api-routes)
- [Components](#components)
- [State Management](#state-management)
- [Features Guide](#features-guide)
- [Contributing](#contributing)

## ✨ Features

### Authentication
- User sign up and login with JWT authentication
- Secure password hashing with bcryptjs
- Cookie-based session management
- Profile creation and updates

### Real-Time Messaging
- Live message sending and receiving using Socket.io
- Message persistence in MongoDB
- Show typing indicators (ready to implement)
- Message history with selected users

### User Management
- View all registered users
- Online status indicators
- User profiles with profile pictures
- Profile picture upload to Cloudinary

### Theme Customization
- 32 beautiful UI themes (DaisyUI themes)
- Dark mode, light mode, and specialty themes
- Theme preference saved to localStorage
- Instant theme switching across the app

### Responsive Design
- Mobile-friendly interface
- Responsive sidebar and chat container
- Works seamlessly on all screen sizes

## 🛠 Tech Stack

### Frontend
- **React 19** - UI framework
- **Vite** - Build tool and dev server
- **Tailwind CSS** - Styling
- **DaisyUI** - Component library
- **Socket.io Client** - Real-time communication
- **Zustand** - State management
- **Axios** - HTTP client
- **React Router** - Navigation
- **Lucide React** - Icons
- **React Hot Toast** - Notifications

### Backend
- **Node.js** - Runtime
- **Express 5** - Web framework
- **MongoDB** - Database
- **Mongoose** - ODM
- **Socket.io** - Real-time communication
- **JWT** - Authentication
- **bcryptjs** - Password hashing
- **Cloudinary** - Image hosting
- **Nodemon** - Development tool

## 📁 Project Structure

```
Realtime_Chat_App/
├── backend/
│   ├── src/
│   │   ├── index.js                 # Entry point
│   │   ├── controllers/
│   │   │   ├── auth.controller.js   # Auth logic
│   │   │   └── message.controller.js # Message logic
│   │   ├── lib/
│   │   │   ├── cloudinary.js        # Image upload config
│   │   │   ├── db.js                # Database connection
│   │   │   ├── socket.js            # Socket.io setup
│   │   │   └── utils.js             # Utilities
│   │   ├── middleware/
│   │   │   └── auth.middleware.js   # JWT verification
│   │   ├── models/
│   │   │   ├── user.model.js        # User schema
│   │   │   └── message.model.js     # Message schema
│   │   ├── routes/
│   │   │   ├── auth.route.js        # Auth endpoints
│   │   │   └── message.route.js     # Message endpoints
│   │   └── seeds/
│   │       └── user.seed.js         # Database seeding
│   └── package.json
│
├── frontend/
│   ├── src/
│   │   ├── main.jsx                 # Entry point
│   │   ├── App.jsx                  # Main App component
│   │   ├── App.css
│   │   ├── index.css
│   │   ├── components/
│   │   │   ├── Navbar.jsx           # Navigation bar
│   │   │   ├── ChatContainer.jsx    # Chat messages area
│   │   │   ├── ChatHeader.jsx       # Chat header
│   │   │   ├── MessageInput.jsx     # Message input
│   │   │   ├── Sidebar.jsx          # Users list
│   │   │   ├── NoChatSelected.jsx   # Empty state
│   │   │   ├── AuthImagePattern.jsx # Auth pages pattern
│   │   │   └── skeletons/           # Loading skeletons
│   │   ├── pages/
│   │   │   ├── HomePage.jsx         # Main chat page
│   │   │   ├── LoginPage.jsx        # Login page
│   │   │   ├── SignUpPage.jsx       # Sign up page
│   │   │   ├── ProfilePage.jsx      # User profile
│   │   │   └── SettingsPage.jsx     # Settings & themes
│   │   ├── store/
│   │   │   ├── useAuthStore.js      # Auth state
│   │   │   ├── useChatStore.js      # Chat state
│   │   │   └── useThemeStore.js     # Theme state
│   │   └── lib/
│   │       ├── axios.js             # Axios config
│   │       └── utils.js             # Utilities
│   ├── package.json
│   ├── vite.config.js
│   ├── tailwind.config.js
│   ├── eslint.config.js
│   └── index.html
│
└── README.md

```

## 📦 Prerequisites

- **Node.js** (v14 or higher)
- **npm** or **yarn**
- **MongoDB** (local or MongoDB Atlas)
- **Cloudinary Account** (for image uploads)

## 🚀 Installation

### 1. Clone the Repository

```bash
git clone <repository-url>
cd Realtime_Chat_App
```

### 2. Backend Setup

```bash
cd backend
npm install
```

### 3. Frontend Setup

```bash
cd ../frontend
npm install
```

## ⚙️ Configuration

### Backend Environment Variables

Create a `.env` file in the `backend` directory:

```env
# Database
MONGODB_URI=YOUR_MONGODB_CONNECTION_STRING

# Server
PORT=5001
NODE_ENV=development

# JWT
JWT_SECRET=your_jwt_secret_key_here

# Cloudinary
CLOUDINARY_CLOUD_NAME=your_cloud_name
CLOUDINARY_API_KEY=your_api_key
CLOUDINARY_API_SECRET=your_api_secret
```

> ⚠️ Do not commit real credentials. Keep this file in `.gitignore` and regenerate/rotate any exposed secrets immediately.

### Frontend Configuration

The frontend is pre-configured to connect to `http://localhost:5001`. If you need to change this, update the `BASE_URL` in [frontend/src/store/useAuthStore.js](frontend/src/store/useAuthStore.js).

## 🎯 Running the Application

### Option 1: Run Both Backend and Frontend

**Terminal 1 - Backend:**
```bash
cd backend
npm run dev
```

**Terminal 2 - Frontend:**
```bash
cd frontend
npm run dev
```

Backend will run on `http://localhost:5001`
Frontend will run on `http://localhost:5173`

### Option 2: Production Build

Frontend:
```bash
cd frontend
npm run build
npm run preview
```

## 📡 API Routes

### Authentication Routes
- `POST /auth/signup` - Register a new user
- `POST /auth/login` - Login user
- `POST /auth/logout` - Logout user
- `GET /auth/check` - Check authentication status
- `PUT /auth/update-profile` - Update user profile

### Message Routes
- `GET /messages/users` - Get list of all users
- `GET /messages/:userId` - Get chat history with a user
- `POST /messages/send/:userId` - Send a message

## 🧩 Components

### Pages
- **HomePage** - Main chat interface
- **LoginPage** - User login
- **SignUpPage** - User registration
- **ProfilePage** - Edit user profile
- **SettingsPage** - Customize theme

### Components
- **Navbar** - Top navigation bar
- **Sidebar** - Users list and chat selection
- **ChatContainer** - Message display area
- **ChatHeader** - Current chat info
- **MessageInput** - Message composition
- **NoChatSelected** - Empty state
- **AuthImagePattern** - Auth pages decoration

## 📊 State Management

The app uses **Zustand** for state management:

### useAuthStore
- `authUser` - Current logged-in user
- `isSigningUp`, `isLoggingIn`, `isUpdatingProfile` - Loading states
- `socket` - Socket.io instance
- `onlineUsers` - List of online users

### useChatStore
- `messages` - Chat messages
- `users` - List of users
- `selectedUser` - Currently selected chat user
- `isUsersLoading`, `isMessagesLoading` - Loading states

### useThemeStore
- `theme` - Current theme
- `themes` - Available themes list
- `setTheme()` - Change theme function

## 🎨 Features Guide

### Theme Customization
1. Navigate to **Settings** page
2. Choose from 32 available themes
3. Click on any theme to apply it instantly
4. Your preference is automatically saved

### Sending Messages
1. Select a user from the sidebar
2. Type your message in the input field
3. Press Enter or click Send
4. Message appears instantly for both users

### Profile Management
1. Go to **Profile** page
2. Upload a profile picture
3. Update your information
4. Save changes

## 🤝 Contributing

Contributions are welcome! Feel free to submit issues and pull requests.

## 📄 License

This project is licensed under the **ISC License**.

---

**Made with ❤️ using React and Node.js**