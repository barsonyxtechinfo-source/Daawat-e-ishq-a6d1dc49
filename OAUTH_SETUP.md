# OAuth Authentication Setup Guide

This guide will help you set up Google and Facebook OAuth authentication for your Daawat-E-Ishq restaurant website.

## Prerequisites

- Node.js and npm installed
- MongoDB database running
- Your website running on localhost:3000

## Step 1: Install Dependencies

First, install the required packages for the server:

```bash
cd server
npm install axios
```

## Step 2: Google OAuth Setup

### 1. Create Google Cloud Project
1. Go to [Google Cloud Console](https://console.cloud.google.com/)
2. Create a new project or select an existing one
3. Enable the Google+ API (or Google Identity API)

### 2. Create OAuth 2.0 Credentials
1. Go to "APIs & Services" → "Credentials"
2. Click "Create Credentials" → "OAuth 2.0 Client ID"
3. Choose "Web application" as the application type
4. Add authorized origins:
   - `http://localhost:3000`
   - `http://localhost:5000`
5. Add authorized redirect URIs:
   - `http://localhost:3000`
   - `http://localhost:3000/`
6. Copy the Client ID

### 3. Update Configuration
Open `frontend/src/config/oauth.js` and replace `YOUR_GOOGLE_CLIENT_ID` with your actual Google Client ID.

## Step 3: Facebook OAuth Setup

### 1. Create Facebook App
1. Go to [Facebook Developers](https://developers.facebook.com/)
2. Click "Create App"
3. Choose "Consumer" as the app type
4. Fill in the required information

### 2. Add Facebook Login
1. In your app dashboard, click "Add Product"
2. Find "Facebook Login" and click "Set Up"
3. Choose "Web" as the platform
4. Add your site URL: `http://localhost:3000`

### 3. Configure OAuth Settings
1. Go to "Facebook Login" → "Settings"
2. Add Valid OAuth Redirect URIs:
   - `http://localhost:3000`
   - `http://localhost:3000/`
3. Copy the App ID from the Basic Settings

### 4. Update Configuration
Open `frontend/src/config/oauth.js` and replace `YOUR_FACEBOOK_APP_ID` with your actual Facebook App ID.

## Step 4: Start Your Application

### Start the Server
```bash
cd server
npm start
```

### Start the Frontend
```bash
cd frontend
npm start
```

## Step 5: Test OAuth Login

1. Open your website at `http://localhost:3000`
2. Go to the login page
3. Click on "Google" or "Facebook" buttons
4. Complete the OAuth flow
5. You should be redirected back to your website and logged in

## Troubleshooting

### Common Issues:

1. **"Invalid Client ID" Error**
   - Make sure you've copied the correct Client ID/App ID
   - Verify the authorized origins and redirect URIs are correct

2. **"Redirect URI Mismatch" Error**
   - Check that your redirect URIs exactly match what's configured in Google/Facebook
   - Include both `http://localhost:3000` and `http://localhost:3000/`

3. **"App Not Found" Error (Facebook)**
   - Make sure your Facebook app is in "Development" mode
   - Add your Facebook account as a test user

4. **CORS Errors**
   - Ensure your server is running on port 5000
   - Check that CORS is properly configured in your server

### Development vs Production

For production deployment:
1. Update the authorized origins and redirect URIs to your production domain
2. Set your Facebook app to "Live" mode
3. Update the OAuth configuration with production URLs

## Security Notes

- Never commit your OAuth credentials to version control
- Use environment variables for production deployments
- Regularly rotate your OAuth credentials
- Implement proper session management and token validation

## Additional Features

The OAuth implementation includes:
- Automatic user creation for new OAuth users
- Profile picture import from Google/Facebook
- Account linking for existing users
- Secure token generation and validation
- Error handling and user feedback

Your OAuth authentication is now ready to use! 🎉
