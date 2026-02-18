# Vercel Deployment Setup Guide for Daawat-E-Ishq

## Overview
Your website has two parts:
- **Frontend** (React): Deployed on Vercel
- **Backend** (Node.js): Can be deployed separately (Render, Railway, Heroku, AWS, etc.)

---

## Step 1: Verify GitHub Connection

✅ Your repository is already connected: `soumyo1234/daawat-e-ishq`

---

## Step 2: Configure Vercel Project Settings

### In Vercel Dashboard:

1. **Select your project** → Click **Settings**

2. **General Settings:**
   - Project Name: `daawat-e-ishq`
   - Framework Preset: `Create React App` ✓

3. **Build & Development Settings:**
   - **Root Directory:** `./frontend` (NOT `./`)
   - **Build Command:** `npm run build`
   - **Output Directory:** `build`
   - **Install Command:** `npm install`

4. **Click Save**

---

## Step 3: Add Environment Variables in Vercel

**Path:** Settings → Environment Variables

Add these variables (they must start with `REACT_APP_` to be accessible in frontend):

| Variable | Value | Where to Get |
|----------|-------|--------------|
| `REACT_APP_API_URL` | `https://your-backend-api.com` | Your backend deployment URL |
| `REACT_APP_GOOGLE_CLIENT_ID` | `258365914995-g3taerkv9uu556871to1fu5qd1to88sr.apps.googleusercontent.com` | From Google Cloud Console |
| `REACT_APP_FACEBOOK_APP_ID` | Your Facebook App ID | From Facebook Developer Console |

**Note:** Leave the Google ID as-is (it's already configured). Update the Facebook ID if you have one.

---

## Step 4: Deploy

1. Go to **Deployments** tab
2. Click **Deploy**
3. Wait for build to complete (usually 2-5 minutes)
4. Once successful, your site will be live at: `https://daawat-e-ishq.vercel.app`

---

## Step 5: Backend Deployment (IMPORTANT)

Your backend API needs to be deployed separately. Options:

### Option A: Render (Recommended)
1. Go to [render.com](https://render.com)
2. Create account
3. Connect GitHub
4. Create New → Web Service
5. Select `soumyo1234/daawat-e-ishq-backend`
6. Settings:
   - Runtime: `Node`
   - Build Command: `npm install`
   - Start Command: `npm start`
7. Add Environment Variables:
   - `MONGO_URI`
   - `JWT_SECRET`
   - `PORT=8000`
   - `FRONTEND_URL=https://daawat-e-ishq.vercel.app`
   - SMTP credentials for emails

### Option B: Railway
1. Go to [railway.app](https://railway.app)
2. Login with GitHub
3. Create New Project
4. Deploy from GitHub
5. Select your backend repo
6. Add environment variables (same as above)

### Option C: Heroku (Free tier no longer available, but if using paid)
Similar process to above platforms.

---

## Step 6: Update CORS in Backend

Once backend URL is obtained, update [server/app.js](../server/app.js):

```javascript
const allowedOrigins = [
  'http://localhost:3000',
  'https://daawat-e-ishq.vercel.app',  // Add your Vercel URL
  'https://your-backend-api.com'        // Your backend URL
];
```

---

## Step 7: Test Everything

### Frontend: https://daawat-e-ishq.vercel.app
- ✅ Pages load
- ✅ Navigation works
- ✅ Menu loads (calls `/api/menu`)
- ✅ Login page loads

### Backend: https://your-backend-api.com
- Test: `GET /` → Should return status OK
- Test: `POST /api/auth/login` → Should work
- Test: `GET /api/menu` → Should return menu items

---

## Common Issues & Solutions

### Issue 1: "REACT_APP_API_URL is undefined"
**Solution:** 
- Env variables must be added BEFORE deployment
- Redeploy after adding env variables
- Variables are built into the app at build time

### Issue 2: CORS Errors
**Solution:**
- Make sure backend has `https://daawat-e-ishq.vercel.app` in CORS origins
- Rebuild backend after updating CORS

### Issue 3: 404 on Frontend Routes
**Solution:**
- Create `public/_redirects` (Netlify) or `vercel.json` with routing config
- Already configured in `vercel.json` file

### Issue 4: Slow Performance
**Solution:**
- Check network tab in DevTools
- Optimize images
- Use Vercel Analytics to identify bottlenecks

---

## File Structure for Deployment

```
daawat-e-ishq/
├── frontend/                    ← Deploy this on Vercel
│   ├── src/
│   ├── public/
│   ├── package.json
│   └── build/ (generated after npm run build)
├── server/                      ← Deploy this on Render/Railway
│   ├── routes/
│   ├── models/
│   ├── controllers/
│   ├── package.json
│   ├── server.js
│   └── .env
├── vercel.json                  ← Vercel configuration
└── package.json                 ← Root package (not deployed)
```

---

## Deployment Checklist

- [ ] GitHub repository connected to Vercel
- [ ] Root Directory set to `./frontend`
- [ ] Environment variables added (REACT_APP_API_URL, etc.)
- [ ] Backend deployed and accessible
- [ ] CORS origins updated in backend
- [ ] First deployment successful
- [ ] Frontend pages loading correctly
- [ ] API calls working (menu, auth, etc.)
- [ ] Custom domain configured (optional)
- [ ] Analytics enabled (optional)

---

## Useful Commands

**Local testing before deploying:**
```bash
# Frontend
cd frontend
npm install
npm run build    # Test build locally
npm start        # Run locally

# Backend (separate terminal)
cd server
npm install
npm start        # Make sure .env is configured
```

**View Vercel logs:**
- Dashboard → Project → Deployments → Select deployment → View logs

**Rebuild/Redeploy:**
- Git push to main branch → Vercel auto-deploys
- Or manually click "Redeploy" in Vercel dashboard

---

## Domain Setup (Optional)

To use a custom domain like `www.daawat-e-ishq.com`:
1. Settings → Domains
2. Add your domain
3. Update DNS records at your domain registrar
4. Vercel provides exact DNS settings to use

---

## Next Steps After Deployment

1. Test all features thoroughly
2. Set up error monitoring (Sentry.io)
3. Configure analytics
4. Set up auto-backups for MongoDB
5. Monitor Vercel Analytics & Performance
6. Set up CI/CD notifications

---

For questions: Check Vercel docs at https://vercel.com/docs
