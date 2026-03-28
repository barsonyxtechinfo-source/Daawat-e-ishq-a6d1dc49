# 🍜 Daawat-e-Ishq Restaurant Website

**A full-stack restaurant management and ordering platform with user authentication, menu management, reservations, and admin dashboard.**

---

## 📋 Table of Contents

- [Project Overview](#project-overview)
- [Features](#features)
- [Tech Stack](#tech-stack)
- [Project Structure](#project-structure)
- [Installation & Setup](#installation--setup)
- [Environment Variables](#environment-variables)
- [Running the Project](#running-the-project)
- [User Features](#user-features)
- [Admin Features](#admin-features)
- [API Endpoints](#api-endpoints)
- [Database Schema](#database-schema)
- [Authentication](#authentication)
- [Deployment](#deployment)
- [Troubleshooting](#troubleshooting)
- [Contributing](#contributing)

---

## 🎯 Project Overview

**Daawat-e-Ishq** is a modern restaurant management system designed to provide a seamless dining experience. It enables customers to:
- Browse and order food online
- Make restaurant reservations
- Track orders
- Leave reviews and ratings

And restaurant administrators to:
- Manage menu items and pricing
- View and manage customer orders
- Track reservations
- Analyze business metrics
- Manage admin accounts

The application is built with **React** (frontend) and **Node.js/Express** (backend) with MongoDB as the database, deployed on **Vercel** (frontend) and cloud hosting (backend).

---

## ✨ Features

### 👤 User Features
- ✅ User registration and login (with Google OAuth support)
- ✅ Browse restaurant menu with category filtering
- ✅ Add items to cart and wishlist
- ✅ Secure checkout and payment
- ✅ Order history and status tracking
- ✅ Make restaurant reservations
- ✅ Leave reviews and ratings
- ✅ User profile management
- ✅ Search functionality
- ✅ Responsive mobile-friendly design

### 🔐 Admin Features
- ✅ Admin authentication (separate from users)
- ✅ Menu management (create, edit, delete items)
- ✅ Order management (view, update order status)
- ✅ Reservation management (view, manage bookings)
- ✅ Business analytics and dashboard
- ✅ Admin account management

### 🛠 Technical Features
- ✅ JWT-based authentication
- ✅ Google OAuth integration
- ✅ CORS-enabled API
- ✅ Password hashing with bcryptjs
- ✅ Email notifications (Nodemailer)
- ✅ State management with React Context
- ✅ Tailwind CSS styling
- ✅ MongoDB document validation

---

## 🏗 Tech Stack

### Frontend
| Technology | Version | Purpose |
|-----------|---------|---------|
| **React** | 18+ | UI library & component framework |
| **React Router** | Latest | Client-side routing |
| **Tailwind CSS** | Latest | Utility-first styling |
| **Axios** | ^1.13.2 | HTTP client for API calls |
| **React Context API** | Built-in | State management |

### Backend
| Technology | Version | Purpose |
|-----------|---------|---------|
| **Node.js** | 18+ | JavaScript runtime |
| **Express.js** | ^5.1.0 | Web application framework |
| **MongoDB** | Latest | NoSQL database |
| **Mongoose** | ^8.17.0 | MongoDB ODM |
| **JWT** | ^9.0.2 | Authentication tokens |
| **bcryptjs** | ^3.0.2 | Password hashing |
| **CORS** | ^2.8.5 | Cross-origin requests |
| **Nodemailer** | ^6.9.4 | Email service |
| **Nodemon** | ^3.1.10 | Development auto-reload |

### Deployment
- **Frontend**: Vercel
- **Backend**: Node.js server (cloud hosted)
- **Database**: MongoDB Atlas

---

## 📁 Project Structure

```
daawat-e-ishq/
├── frontend/                          # React frontend application
│   ├── public/                        # Static files
│   ├── src/
│   │   ├── components/                # Reusable React components
│   │   │   ├── Navbar.jsx
│   │   │   ├── Footer.jsx
│   │   │   ├── Dashboard.jsx
│   │   │   ├── HeroSection.jsx
│   │   │   ├── CategoryFilter.jsx
│   │   │   ├── ReviewCard.jsx
│   │   │   └── menu/                  # Menu-related components
│   │   ├── pages/                     # Page components
│   │   │   ├── Home.jsx
│   │   │   ├── Menu.jsx
│   │   │   ├── Cart.jsx
│   │   │   ├── Checkout.jsx
│   │   │   ├── Profile.jsx
│   │   │   ├── Reservations.jsx
│   │   │   ├── Reviews.jsx
│   │   │   ├── Blog.jsx
│   │   │   ├── Contact.jsx
│   │   │   └── Auth/                  # Authentication pages
│   │   ├── admin/                     # Admin panel components
│   │   │   ├── AdminLayout.jsx
│   │   │   ├── AdminLogin.jsx
│   │   │   ├── RestaurantDashboard.jsx
│   │   │   ├── MenuManagement.jsx
│   │   │   ├── OrderManagement.jsx
│   │   │   ├── Analytics.jsx
│   │   │   └── AdminSidebar.jsx
│   │   ├── context/                   # React Context for state management
│   │   │   ├── AuthContext.jsx        # User authentication
│   │   │   ├── AdminAuthContext.jsx   # Admin authentication
│   │   │   ├── CartContext.jsx        # Shopping cart state
│   │   │   ├── MenuContext.jsx        # Menu data
│   │   │   ├── WishlistContext.jsx    # Wishlist state
│   │   │   └── ThemeContext.jsx       # Theme (dark/light mode)
│   │   ├── utils/
│   │   │   ├── api.js                 # Axios instance for API calls
│   │   │   └── validators.js          # Validation functions
│   │   ├── config/
│   │   │   └── oauth.js               # OAuth configuration
│   │   ├── App.js                     # Main app component
│   │   ├── index.js                   # React entry point
│   │   └── Assets/                    # Images and media
│   ├── package.json
│   └── tailwind.config.js
│
├── server/                            # Node.js/Express backend
│   ├── models/                        # MongoDB schemas
│   │   ├── User.js                    # User model
│   │   ├── Admin.js                   # Admin user model
│   │   ├── MenuItem.js                # Menu items
│   │   ├── Order.js                   # Orders
│   │   ├── Reservation.js             # Table reservations
│   │   └── Review.js                  # Customer reviews
│   ├── routes/                        # API route handlers
│   │   ├── auth.js                    # User authentication
│   │   ├── adminAuth.js               # Admin authentication
│   │   ├── menuRoutes.js              # Menu operations
│   │   ├── orderRoutes.js             # Order operations
│   │   ├── reservationRoutes.js       # Reservation operations
│   │   ├── reviewRoutes.js            # Review operations
│   │   ├── contactRoutes.js           # Contact form
│   │   └── testRoutes.js              # Testing routes
│   ├── controllers/                   # Business logic
│   │   ├── authController.js
│   │   ├── menuController.js
│   │   ├── orderController.js
│   │   └── contactController.js
│   ├── middleware/                    # Express middleware
│   │   └── authMiddleware.js          # JWT verification
│   ├── config/
│   │   └── db.js                      # MongoDB connection
│   ├── utils/
│   │   └── generateToken.js           # JWT token generation
│   ├── scripts/
│   │   └── seedAdmin.js               # Initialize admin user
│   ├── server.js                      # Main server entry point
│   ├── package.json
│   └── .env                           # Environment variables (not in repo)
│
├── OAUTH_SETUP.md                     # OAuth configuration guide
├── TASKS_README.md                    # Development roadmap
├── vercel.json                        # Vercel deployment config
├── package.json                       # Root package.json
└── README.md                          # This file
```

---

## 🚀 Installation & Setup

### Prerequisites
- Node.js 18+ installed
- npm or yarn package manager
- MongoDB account (Atlas recommended)
- Git installed

### Step 1: Clone the Repository

```bash
git clone https://github.com/barsonyxtechinfo-source/Daawat-e-ishq.git
cd daawat-e-ishq
```

### Step 2: Install Backend Dependencies

```bash
cd server
npm install
```

### Step 3: Install Frontend Dependencies

```bash
cd ../frontend
npm install
```

### Step 4: Create Environment Variables

Create a `.env` file in the `server` directory:

```env
# Database
MONGO_URI=mongodb+srv://username:password@cluster.mongodb.net/daawat-e-ishq?retryWrites=true&w=majority

# JWT
JWT_SECRET=your_super_secure_random_secret_key_here

# Server Config
PORT=5000
NODE_ENV=development

# Frontend URL
FRONTEND_URL=http://localhost:3000

# Google OAuth (Optional)
GOOGLE_CLIENT_ID=your_google_client_id_here

# Email Service (Optional)
EMAIL_USER=your_email@gmail.com
EMAIL_PASSWORD=your_email_password
```

### Step 5: Seed Admin User

```bash
cd server
npm run seed
```

This creates default admin credentials:
- **Email**: `admin@admin.com`
- **Password**: `admin123`

⚠️ **Change these credentials immediately in production!**

---

## 🔧 Environment Variables

### Required Variables

| Variable | Description | Example |
|----------|-------------|---------|
| `MONGO_URI` | MongoDB connection string | `mongodb+srv://user:pass@cluster.mongodb.net/db` |
| `JWT_SECRET` | Secret key for JWT signing | Any random string (64+ chars recommended) |
| `PORT` | Server port | `5000` |

### Optional Variables

| Variable | Description | Example |
|----------|-------------|---------|
| `NODE_ENV` | Environment mode | `development` or `production` |
| `FRONTEND_URL` | Frontend application URL | `http://localhost:3000` |
| `GOOGLE_CLIENT_ID` | Google OAuth client ID | From Google Cloud Console |
| `EMAIL_USER` | Email for notifications | `your-email@gmail.com` |
| `EMAIL_PASSWORD` | Email password/app password | From email provider |

---

## ▶️ Running the Project

### Development Mode

**Terminal 1 - Start Backend Server:**
```bash
cd server
npm run dev
```
Backend will run on `http://localhost:5000`

**Terminal 2 - Start Frontend Development Server:**
```bash
cd frontend
npm start
```
Frontend will run on `http://localhost:3000`

### Production Build

**Build frontend:**
```bash
cd frontend
npm run build
```

**Start production server:**
```bash
cd server
npm start
```

---

## 👥 User Features

### 1. **User Authentication**
- Email/password registration and login
- Google OAuth single sign-on
- JWT token-based sessions
- Password-protected account

### 2. **Menu Browsing**
- View all available menu items
- Filter by category
- Search for specific dishes
- See price and descriptions

### 3. **Shopping Cart**
- Add/remove items from cart
- Adjust quantities
- Real-time price calculation
- Persistent cart state

### 4. **Wishlist**
- Save favorite items
- Quick access to saved items
- One-click ordering from wishlist

### 5. **Ordering**
- Secure checkout process
- Order confirmation
- Order history and status tracking
- Order details retrieval

### 6. **Reservations**
- Book table in advance
- Select date and time
- Specify number of guests
- Optional special requests

### 7. **Reviews & Ratings**
- Leave 5-star ratings
- Write detailed reviews
- See all customer reviews
- Public feedback system

### 8. **User Profile**
- View profile information
- Edit personal details
- View order history
- Manage preferences

---

## 🎛️ Admin Features

### 1. **Admin Login**
- Separate admin authentication
- Role-based access control
- Secure password storage

### 2. **Menu Management**
- Create new menu items
- Edit existing items (name, price, description, image)
- Delete discontinued items
- Organize by categories

### 3. **Order Management**
- View all customer orders
- Update order status (pending → completed → cancelled)
- See order details and items
- Track order history

### 4. **Reservation Management**
- View all table reservations
- Confirm or reject bookings
- See guest details
- Manage reservation timeline

### 5. **Analytics Dashboard**
- View key metrics
- Total orders and revenue
- Customer statistics
- Popular menu items
- Business insights

### 6. **Restaurant Dashboard**
- Quick overview of operations
- Pending orders count
- Upcoming reservations
- System health status

---

## 🔌 API Endpoints

### Authentication Routes

#### User Authentication
```
POST   /api/auth/register          # Register new user
POST   /api/auth/login             # Login user
POST   /api/auth/logout            # Logout user
GET    /api/auth/profile           # Get user profile (protected)
PUT    /api/auth/profile           # Update user profile (protected)
```

#### Admin Authentication
```
POST   /admin/auth/login           # Admin login
GET    /admin/auth/profile         # Get admin profile (protected)
PUT    /admin/auth/profile         # Update admin profile (protected)
PUT    /admin/auth/change-password # Change password (protected)
POST   /admin/auth/logout          # Admin logout (protected)
```

### Menu Routes
```
GET    /api/menu                   # Get all menu items
GET    /api/menu/:id               # Get menu item by ID
POST   /admin/menu                 # Create menu item (admin only)
PUT    /admin/menu/:id             # Update menu item (admin only)
DELETE /admin/menu/:id             # Delete menu item (admin only)
```

### Order Routes
```
POST   /api/orders                 # Create new order (protected)
GET    /api/orders                 # Get user's orders (protected)
GET    /api/orders/:id             # Get order details (protected)
GET    /admin/orders               # Get all orders (admin only)
PUT    /admin/orders/:id           # Update order status (admin only)
```

### Reservation Routes
```
POST   /api/reservations           # Create reservation
GET    /api/reservations           # Get reservations (protected)
PUT    /api/reservations/:id       # Update reservation (protected)
DELETE /api/reservations/:id       # Cancel reservation (protected)
GET    /admin/reservations         # Get all reservations (admin only)
```

### Review Routes
```
GET    /api/reviews                # Get all reviews
POST   /api/reviews                # Create review (protected)
GET    /api/reviews/:id            # Get review details
PUT    /api/reviews/:id            # Update review (protected)
DELETE /api/reviews/:id            # Delete review (protected)
```

### Contact Routes
```
POST   /api/contact                # Send contact form message
```

---

## 🗄️ Database Schema

### User Model
```javascript
{
  _id: ObjectId,
  name: String (required),
  email: String (required, unique),
  password: String (hashed, required),
  phone: String,
  address: String,
  createdAt: Date,
  updatedAt: Date
}
```

### Admin Model
```javascript
{
  _id: ObjectId,
  name: String (required),
  email: String (required, unique),
  password: String (hashed, required),
  role: String (enum: ["admin", "super_admin"]),
  createdAt: Date,
  updatedAt: Date
}
```

### MenuItem Model
```javascript
{
  _id: ObjectId,
  name: String (required),
  description: String,
  price: Number (required),
  image: String (URL),
  category: String,
  available: Boolean (default: true),
  createdAt: Date,
  updatedAt: Date
}
```

### Order Model
```javascript
{
  _id: ObjectId,
  user: ObjectId (ref: User, required),
  items: [
    {
      name: String,
      price: Number,
      quantity: Number
    }
  ],
  total: Number (required),
  status: String (enum: ["pending", "completed", "cancelled"]),
  shippingAddress: String,
  createdAt: Date,
  updatedAt: Date
}
```

### Reservation Model
```javascript
{
  _id: ObjectId,
  name: String (required),
  email: String (required),
  guests: Number (required),
  date: Date (required),
  time: String (required),
  message: String,
  status: String (enum: ["pending", "confirmed", "cancelled"])
}
```

### Review Model
```javascript
{
  _id: ObjectId,
  name: String (required),
  rating: Number (required, 1-5),
  comment: String,
  date: Date (default: now)
}
```

---

## 🔐 Authentication

### How Authentication Works

1. **User Registration**
   - User provides email and password
   - Password is hashed using bcryptjs
   - User record created in MongoDB
   - User can now login

2. **User Login**
   - User provides email and password
   - Password verified against hash
   - JWT token generated and returned
   - Token stored in localStorage (frontend)
   - Token included in subsequent API requests

3. **Admin Login**
   - Separate admin authentication flow
   - Validates admin credentials
   - Issues admin-specific JWT token
   - Admin token required for admin operations

4. **Protected Routes**
   - Middleware checks for valid JWT token
   - Token verified using JWT_SECRET
   - User/admin ID extracted from token
   - Request allowed or denied accordingly

### JWT Token Structure
```javascript
{
  userId: "user_id_here",
  email: "user@example.com",
  role: "user", // or "admin"
  iat: 1234567890,
  exp: 1234571490
}
```

### Google OAuth Integration
- User clicks "Sign in with Google"
- Google authentication dialog appears
- User authorizes app
- Google returns user info
- User account created/logged in automatically
- JWT token issued for session

---

## 🌐 Deployment

### Frontend Deployment (Vercel)

1. Push code to GitHub
2. Connect GitHub repo to Vercel
3. Set environment variables in Vercel dashboard
4. Deploy automatically on push to main branch

**Live Frontend**: https://daawat-e-ishq-frontend.vercel.app

### Backend Deployment

Deploy on cloud services like:
- Heroku (PaaS)
- AWS EC2 (IaaS)
- DigitalOcean (VPS)
- Railway
- Render

**Steps:**
1. Create account on hosting platform
2. Add .env file with production variables
3. Deploy Node.js server
4. Update FRONTEND_URL and API endpoints

### MongoDB Atlas Setup

1. Create account at MongoDB Atlas
2. Create cluster
3. Generate connection string
4. Add IP whitelist
5. Use connection string in MONGO_URI

---

## 🐛 Troubleshooting

### Frontend Issues

**Problem**: `Cannot GET /` on localhost:3000
- **Solution**: Ensure npm start is running in frontend directory

**Problem**: API calls return 403 or 404
- **Solution**: Check backend is running on port 5000
- Check CORS configuration in server.js
- Verify API calls use correct endpoints

**Problem**: Token not persisting after refresh
- **Solution**: Check localStorage is enabled
- Verify token is being saved: `localStorage.getItem('token')`

### Backend Issues

**Problem**: `ECONNREFUSED` - Cannot connect to MongoDB
- **Solution**: Check MONGO_URI is correct
- Verify MongoDB Atlas cluster is active
- Check IP whitelist includes your IP

**Problem**: `Cannot find module 'xyz'`
- **Solution**: Run `npm install` in server directory
- Delete node_modules and run `npm install` again

**Problem**: JWT token expired
- **Solution**: User needs to login again
- Token expires after set time (check JWT_SECRET)
- Implement refresh token mechanism

### Authentication Issues

**Problem**: Admin cannot login
- **Solution**: Run `npm run seed` to create admin
- Check admin credentials in .env or database
- Verify CORS allows credentials

**Problem**: Google OAuth not working
- **Solution**: Verify GOOGLE_CLIENT_ID is correct
- Check OAuth credentials in Google Cloud Console
- Ensure authorized redirect URIs are configured

---

## 📝 Development Roadmap

### High Priority
- [ ] Fix auth token handling and interceptors
- [ ] Replace local menu data with API
- [ ] Standardize roles and auth checks
- [ ] Configure CORS and credentials
- [ ] Implement responsive design

### Medium Priority
- [ ] Add form validation (express-validator)
- [ ] Standardize error responses
- [ ] Add unit tests
- [ ] Implement logging

### Low Priority
- [ ] Add payment gateway
- [ ] Implement email notifications
- [ ] Add analytics tracking
- [ ] Performance optimization

---

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch: `git checkout -b feature/amazing-feature`
3. Commit changes: `git commit -m 'Add amazing feature'`
4. Push to branch: `git push origin feature/amazing-feature`
5. Open a Pull Request

### Code Standards
- Use consistent naming conventions
- Add comments for complex logic
- Test features before submitting PR
- Keep commits atomic and descriptive

---

## 📄 License

This project is private and not licensed for public use.

---

## 👨‍💼 Contact & Support

For questions or issues:
- Create an GitHub issue
- Contact development team
- Check TASKS_README.md for current development status

---

## 🎉 Acknowledgments

Built with ❤️ using modern web technologies and best practices.

**Last Updated**: March 29, 2026
**Version**: 1.0.0
**Repository**: https://github.com/barsonyxtechinfo-source/Daawat-e-ishq


# Getting Started with Create React App

This project was bootstrapped with [Create React App](https://github.com/Dawaat_E_Ishq).

## Available Scripts

In the project directory, you can run:

### `npm start`

Runs the app in the development mode.\

The page will reload when you make changes.\
You may also see any lint errors in the console.

### `npm test`

Launches the test runner in the interactive watch mode.\
See the section about [running tests](https://facebook.github.io/create-react-app/docs/running-tests) for more information.

### `npm start`

Builds the app for production to the `build` folder.\
It correctly bundles React in production mode and optimizes the build for the best performance.

The build is minified and the filenames include the hashes.\
Your app is ready to be deployed!

See the section about [deployment](https://facebook.github.io/create-react-app/docs/deployment) for more information.

### `npm run eject`

**Note: this is a one-way operation. Once you `eject`, you can't go back!**

If you aren't satisfied with the build tool and configuration choices, you can `eject` at any time. This command will remove the single build dependency from your project.

Instead, it will copy all the configuration files and the transitive dependencies (webpack, Babel, ESLint, etc) right into your project so you have full control over them. All of the commands except `eject` will still work, but they will point to the copied scripts so you can tweak them. At this point you're on your own.

You don't have to ever use `eject`. The curated feature set is suitable for small and middle deployments, and you shouldn't feel obligated to use this feature. However we understand that this tool wouldn't be useful if you couldn't customize it when you are ready for it.

## Learn More

You can learn more in the [Create React App documentation](https://facebook.github.io/create-react-app/docs/getting-started).

To learn React, check out the [React documentation](https://reactjs.org/).

### Code Splitting

This section has moved here: [https://facebook.github.io/create-react-app/docs/code-splitting](https://facebook.github.io/create-react-app/docs/code-splitting)

### Analyzing the Bundle Size

This section has moved here: [https://facebook.github.io/create-react-app/docs/analyzing-the-bundle-size](https://facebook.github.io/create-react-app/docs/analyzing-the-bundle-size)

### Making a Progressive Web App

This section has moved here: [https://facebook.github.io/create-react-app/docs/making-a-progressive-web-app](https://facebook.github.io/create-react-app/docs/making-a-progressive-web-app)

### Advanced Configuration

This section has moved here: [https://facebook.github.io/create-react-app/docs/advanced-configuration](https://facebook.github.io/create-react-app/docs/advanced-configuration)

### Deployment

This section has moved here: [https://facebook.github.io/create-react-app/docs/deployment](https://facebook.github.io/create-react-app/docs/deployment)

### `npm run build` fails to minify

This section has moved here: [https://facebook.github.io/create-react-app/docs/troubleshooting#npm-run-build-fails-to-minify](https://facebook.github.io/create-react-app/docs/troubleshooting#npm-run-build-fails-to-minify)
