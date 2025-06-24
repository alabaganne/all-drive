# All-Drive

A comprehensive cloud storage management application that allows users to connect and manage multiple cloud storage services (Google Drive, OneDrive, Dropbox, MEGA) from a single unified interface.

## 🚀 Features

- **Multi-Cloud Integration**: Connect and manage multiple cloud storage services
- **Unified File Management**: Browse, organize, and manage files across different cloud providers
- **User Authentication**: Secure login and registration system
- **File Organization**: Create folders, categorize files, and organize content
- **Search Functionality**: Search across all connected drives
- **File Sharing**: Share files and folders with other users
- **Recycle Bin**: Recover deleted files
- **Modern UI**: Beautiful, responsive interface built with React and Tailwind CSS
- **Real-time Updates**: Live synchronization with cloud storage services

## 🖼️ Screenshots

Dashboard view:

![Dashboard](./screenshots/dashboard.png)

More screenshots can be found in the [screenshots](./screenshots) folder.

## 🛠️ Tech Stack

### Frontend (Client)
- **React 18** - UI framework
- **TypeScript** - Type safety and better development experience
- **Vite** - Build tool and development server
- **React Router DOM** - Client-side routing
- **Tailwind CSS** - Utility-first CSS framework
- **Framer Motion** - Animation library
- **React Icons** - Icon library
- **Axios** - HTTP client for API requests
- **React Toastify** - Toast notifications
- **React Dropzone** - File upload handling
- **Chart.js & React-Chartjs-2** - Data visualization
- **LocalForage** - Local storage management

### Backend (Server)
- **Node.js** - Runtime environment
- **Express.js** - Web framework
- **MongoDB** - NoSQL database with Mongoose ODM
- **JWT** - Authentication tokens
- **bcrypt** - Password hashing
- **Google APIs** - Google Drive integration
- **Multer** - File upload middleware
- **CORS** - Cross-origin resource sharing
- **dotenv** - Environment variable management

## 📁 Project Structure

```
all-drive/
├── client/                          # Frontend React application
│   ├── public/                      # Static assets
│   │   ├── icons/                   # SVG icons for drives and file types
│   │   └── react.svg
│   │   ├── components/              # Reusable React components
│   │   │   ├── shared/              # Shared components
│   │   │   │   ├── cards/           # Card components for drives and files
│   │   │   │   ├── Navbar.tsx       # Navigation bar
│   │   │   │   ├── SidebarLeft.tsx  # Left sidebar
│   │   │   │   └── SidebarRight.tsx # Right sidebar
│   │   │   ├── Button.tsx           # Button component
│   │   │   ├── Input.tsx            # Input component
│   │   │   ├── Layout.tsx           # Main layout wrapper
│   │   │   └── modal/               # Modal components
│   │   ├── context/                 # React context providers
│   │   │   ├── auth-context.tsx     # Authentication context
│   │   │   └── modal-context.tsx    # Modal state management
│   │   ├── data/                    # Static data and mock files
│   │   │   └── static/mock/         # Mock data for development
│   │   ├── libs/                    # Utility libraries
│   │   │   ├── helpers/             # Helper functions
│   │   │   └── hooks/               # Custom React hooks
│   │   ├── pages/                   # Page components
│   │   │   ├── Dashboard.tsx        # Main dashboard
│   │   │   ├── Login.tsx            # Login page
│   │   │   ├── Register.tsx         # Registration page
│   │   │   ├── MyFolders.tsx        # Folders management
│   │   │   ├── AddDrive.tsx         # Add new drive
│   │   │   ├── SharedFiles.tsx      # Shared files view
│   │   │   ├── RecycleBin.tsx       # Recycle bin
│   │   │   └── Search.tsx           # Search functionality
│   │   ├── types/                   # TypeScript type definitions
│   │   │   ├── drives.ts            # Drive-related types
│   │   │   ├── folder.ts            # Folder types
│   │   │   └── items.ts             # File item types
│   │   ├── App.tsx                  # Main App component
│   │   ├── main.tsx                 # Application entry point
│   │   └── router.tsx               # Routing configuration
│   ├── package.json                 # Frontend dependencies
│   ├── tailwind.config.cjs          # Tailwind CSS configuration
│   ├── tsconfig.json                # TypeScript configuration
│   └── vite.config.ts               # Vite configuration
├── server/                          # Backend Node.js application
│   ├── middlewares/                 # Express middlewares
│   │   ├── auth.js                  # Authentication middleware
│   │   └── upload.js                # File upload middleware
│   ├── models/                      # Database models
│   │   ├── user.js                  # User model
│   │   └── drive.js                 # Drive model
│   ├── routes/                      # API routes
│   │   ├── auth.js                  # Authentication routes
│   │   ├── drive.js                 # Drive management routes
│   │   └── user-drive.js            # User-drive relationship routes
│   ├── app.js                       # Main server file
│   ├── google-drive-routes.js       # Google Drive integration
│   ├── db.sql                       # Database schema
│   ├── init-db.js                   # Database initialization
│   └── package.json                 # Backend dependencies
├── docs/                            # Documentation
│   ├── Diagrams/                    # UML diagrams and use cases
│   └── Chapters/                    # Project documentation chapters
└── README.md                        # This file
```

## 🚀 Getting Started

### Prerequisites

- Node.js (v16 or higher)
- npm or yarn
- MongoDB database
- Google Cloud Console account (for Google Drive integration)

### Installation

1. **Clone the repository**
   ```bash
   git clone <repository-url>
   cd all-drive
   ```

2. **Install frontend dependencies**
   ```bash
   cd client
   npm install
   ```

3. **Install backend dependencies**
   ```bash
   cd ../server
   npm install
   ```

4. **Environment Setup**

   Create a `.env` file in the server directory:
   ```env
   # Server Configuration
   PORT=3000
   
   # MongoDB Connection
   MONGODB_URI=mongodb+srv://username:password@cluster.mongodb.net/all-drive
   
   # JWT Configuration
   ACCESS_TOKEN_SECRET=your_jwt_secret_key
   
   # Google Drive API Configuration
   GOOGLE_CLIENT_ID=your_google_client_id
   GOOGLE_CLIENT_SECRET=your_google_client_secret
   GOOGLE_SCOPE=https://www.googleapis.com/auth/drive
   GOOGLE_REDIRECT_URL=http://localhost:3000/auth
   ```

5. **Database Setup**
   ```bash
   cd server
   node init-db.js
   ```

### Running the Application

1. **Start the backend server**
   ```bash
   cd server
   npm run dev
   ```
   The server will start on `http://localhost:3000`

2. **Start the frontend development server**
   ```bash
   cd client
   npm run dev
   ```
   The client will start on `http://localhost:9000`

3. **Build for production**
   ```bash
   cd client
   npm run build
   ```

## 🔧 API Endpoints

### Authentication
- `POST /auth/register` - User registration
- `POST /auth/login` - User login

### Drive Management
- `GET /` - Google Drive OAuth initiation
- `GET /auth` - Google Drive OAuth callback
- `POST /user-drive/getFolders` - Get user folders
- `POST /drive/add` - Add new drive connection

## 🌟 Key Features Explained

### Multi-Cloud Integration
The application supports multiple cloud storage providers:
- **Google Drive**: Full integration with Google Drive API
- **OneDrive**: Microsoft OneDrive integration
- **Dropbox**: Dropbox API integration
- **MEGA**: MEGA cloud storage integration

### File Management
- Browse files and folders across all connected drives
- Upload, download, and delete files
- Create new folders and organize content
- Search functionality across all drives
- File sharing with other users

### User Experience
- Modern, responsive design with Tailwind CSS
- Smooth animations with Framer Motion
- Toast notifications for user feedback
- Loading states and error handling
- Mobile-friendly interface

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add some amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

## 📝 License

This project is licensed under the ISC License.

## 🆘 Support

For support and questions, please open an issue in the repository or contact the development team.
