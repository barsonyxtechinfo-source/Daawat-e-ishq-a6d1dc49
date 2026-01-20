Project: Daawat-e-Ishq — Tasks & Onboarding

Goal
- Make the app reliable (no assumed data), robust (no runtime auth/role errors), and fully responsive.

High-level roadmap (prioritized)
1. Fix auth token handling (in-progress)
   - Add axios interceptor in `frontend/src/utils/api.js` to attach `Authorization: Bearer <token>` from localStorage.
   - Verify all frontend API calls use the `api` instance.
   - Quick verification: Start backend, open browser console, hit a protected endpoint with a stored token and expect 200.

2. Replace local menu data with API
   - Update `MenuContext` to fetch `/api/menu` on load.
   - Provide loading skeletons and graceful error UI.

3. Standardize roles & auth checks
   - Pick a single string for super admin (`superadmin` vs `super_admin`) and update models/middleware.
   - Add tests for admin-protected endpoints.

4. CORS & credentials
   - Decide whether you use cookie-based auth or header-based JWT.
   - If cookies: enable CORS with origin and credentials on server; set cookie flags.
   - If JWT headers: remove withCredentials or keep false.

5. Responsive UI updates
   - Apply Tailwind mobile-first utilities. Key components: Navbar, Menu grid/cards, Cart, Checkout.
   - Add lazy image loading, fluid sizes, and larger touch targets.

6. Validation and error handling
   - Add express-validator and standardized error shapes.

7. QA & smoke tests
   - Add minimal tests and a smoke script for local verification.

How we'll work
- We'll implement tasks one by one. The first task is set to in-progress in the todo list.
- After I implement a task, I'll run a quick local verification and report results.

First task: Fix auth token handling — verification steps
1. Edit `frontend/src/utils/api.js` to attach token via axios interceptor.
2. Search frontend for direct fetch/axios calls and update to use `api` where appropriate.
3. Start server (ensure .env has MONGO_URI and JWT_SECRET) and start frontend.
4. Login via frontend, then inspect network requests to protected endpoints — Authorization header should be present.

If you want me to proceed now, reply "Proceed" and I'll implement task #1 (add interceptor + minimal search for usage) and report back with the exact changes.
