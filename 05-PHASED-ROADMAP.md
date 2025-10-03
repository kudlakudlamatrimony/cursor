# 📅 KUDLA MATRIMONY - PHASED ROADMAP

**Version:** 1.0  
**Date:** October 2, 2025  
**Timeline:** 16-18 weeks to MVP Launch  
**Methodology:** Agile with weekly sprints  

---

## 📋 TABLE OF CONTENTS

1. [Overview](#overview)
2. [Phase 0: Setup & Infrastructure](#phase-0-setup--infrastructure)
3. [Phase 1: MVP Development](#phase-1-mvp-development)
4. [Phase 2: Enhancements](#phase-2-enhancements)
5. [Phase 3: Scale & Growth](#phase-3-scale--growth)
6. [Dependencies Map](#dependencies-map)
7. [Risk Management](#risk-management)

---

## 1. OVERVIEW

### Project Phases

| Phase | Duration | Weeks | Deliverables | Cost |
|-------|----------|-------|--------------|------|
| **Phase 0** | Setup | Week 1 | Infrastructure, skeleton apps | $10/mo |
| **Phase 1** | MVP | Weeks 2-16 | Launch-ready platform | $10-55/mo |
| **Phase 2** | Enhancements | Weeks 17-24 | Advanced features | $55-159/mo |
| **Phase 3** | Scale | Month 7+ | Growth features, mobile apps | $159-300/mo |

### Key Principles

- ✅ **Feature-Complete Sprints:** Each week delivers working features
- ✅ **Daily Updates:** Progress reports with preview links
- ✅ **Weekly Deployments:** Push to production every Friday
- ✅ **Continuous Testing:** Tests written before code
- ✅ **AI-Managed:** I handle all development autonomously

---

## 2. PHASE 0: SETUP & INFRASTRUCTURE

**Duration:** Week 1 (7 days)  
**Goal:** Deployable skeleton apps with all services integrated  

### Week 1: Infrastructure Setup

#### **Day 1-2: Service Account Creation**

**Tasks:**
- [x] Create Vercel account
- [x] Create Railway account  
- [x] Create Neon PostgreSQL database
- [x] Create Upstash Redis database
- [x] Create Sentry projects (web + API)
- [x] Create Better Stack monitors

**Your Actions:**
- Sign up for all services
- Verify emails
- Provide API keys (Cloudinary, Resend, fast2sms, PhonePe)

**Deliverables:**
- All service accounts active
- API keys collected

---

#### **Day 3-4: Repository & CI/CD Setup**

**Tasks:**
- [ ] Create GitHub repository (public)
- [ ] Initialize Turborepo monorepo
- [ ] Set up Next.js app (apps/web)
- [ ] Set up NestJS app (apps/api)
- [ ] Configure shared packages
- [ ] Create GitHub Actions workflows:
  - `deploy-web.yml` (Vercel deployment)
  - `deploy-api.yml` (Railway deployment)
  - `test.yml` (run tests on PR)
  - `lint.yml` (code quality checks)
- [ ] Configure ESLint, Prettier, Husky
- [ ] Set up branch protection rules

**Deliverables:**
- GitHub repo: `https://github.com/[your-username]/kudla-matrimony`
- CI/CD pipelines configured
- Code quality tools active

---

#### **Day 5: Database & Prisma Setup**

**Tasks:**
- [ ] Design complete Prisma schema (20+ models)
- [ ] Configure Prisma client
- [ ] Create initial migration
- [ ] Run migration on Neon database
- [ ] Create seed script:
  - Religions (Hindu, Christian, Muslim)
  - Communities (8 communities from PRD)
  - Sample users (for testing)
- [ ] Test database connections

**Deliverables:**
- `apps/api/prisma/schema.prisma` (complete)
- Database migrated with initial data
- Seed script functional

**Database Tables Created:**
```
✅ users (with auth fields)
✅ profiles (with all fields)
✅ photos
✅ religions
✅ communities
✅ interests
✅ messages
✅ payments
✅ reports
✅ success_stories
✅ contact_messages
✅ activity_logs
```

---

#### **Day 6: Deployment & Integration**

**Tasks:**
- [ ] Connect Vercel to GitHub repo
- [ ] Configure Vercel environment variables
- [ ] Deploy Next.js to Vercel
- [ ] Connect Railway to GitHub repo
- [ ] Configure Railway environment variables
- [ ] Deploy NestJS to Railway
- [ ] Test API health endpoint: `/health`
- [ ] Configure Cloudinary integration
- [ ] Configure Resend integration
- [ ] Configure fast2sms integration
- [ ] Test email sending
- [ ] Test SMS sending

**Deliverables:**
- Frontend live: `https://kudla-matrimony-[hash].vercel.app`
- Backend live: `https://kudla-matrimony-api-[hash].up.railway.app`
- All integrations working

---

#### **Day 7: DNS, Admin User & Verification**

**Tasks:**
- [ ] Update Cloudflare DNS records:
  - `@` → Vercel
  - `www` → Vercel
  - `api` → Railway
- [ ] Configure Cloudflare Email Routing
- [ ] Set up SSL certificates (auto by Cloudflare)
- [ ] Create admin user script
- [ ] Run admin user creation:
  - Email: matrimonykudla@gmail.com
  - Role: SUPER_ADMIN
- [ ] Test admin login
- [ ] Configure Sentry error tracking
- [ ] Set up Better Stack uptime monitoring
- [ ] Run full integration tests
- [ ] Document all credentials

**Deliverables:**
- Production URLs:
  - Frontend: `https://kudlamatrimony.com`
  - API: `https://api.kudlamatrimony.com`
  - Docs: `https://api.kudlamatrimony.com/docs`
- Admin credentials provided to you
- All systems operational ✅

**End of Week 1 Checklist:**
- [x] All services connected
- [x] Database schema deployed
- [x] Apps deployed to production
- [x] DNS configured
- [x] Admin user created
- [x] Monitoring active
- [x] You can log in to admin panel

---

## 3. PHASE 1: MVP DEVELOPMENT

**Duration:** Weeks 2-16 (15 weeks)  
**Goal:** Launch-ready matrimony platform with core features  

### EPIC 1: User Authentication (Weeks 2-3)

#### **Week 2: Registration & Email Verification**

**User Story 1.1:** New User Registration

**Backend Tasks:**
- [ ] Create `AuthModule` with NestJS
- [ ] Implement `POST /api/v1/auth/register` endpoint
- [ ] Email/phone uniqueness validation
- [ ] Password hashing with bcrypt (12 rounds)
- [ ] Generate email verification token (UUID, 24hr expiry)
- [ ] Generate phone OTP (6 digits, 10min expiry)
- [ ] Store tokens in database
- [ ] Create email queue (BullMQ)
- [ ] Create SMS queue (BullMQ)
- [ ] Email processor: Send verification email via Resend
- [ ] SMS processor: Send OTP via fast2sms
- [ ] Implement `POST /api/v1/auth/verify-email`
- [ ] Implement `POST /api/v1/auth/verify-phone`
- [ ] Implement `POST /api/v1/auth/resend-otp`

**Frontend Tasks:**
- [ ] Create `/register` page
- [ ] Build registration form (React Hook Form + Zod):
  - Fields: Name, Email, Phone, Gender, Password
  - Validation: Email format, phone format (10 digits), password strength
- [ ] Display validation errors inline
- [ ] Create `/verify-email` page (token from URL)
- [ ] Create `/verify-phone` page (OTP input)
- [ ] Success/error toasts
- [ ] Redirect flow after verification

**Testing:**
- [ ] Unit tests: Registration validation
- [ ] Integration tests: Full registration flow
- [ ] E2E test: Register → Verify email → Verify phone → Success
- [ ] Test email delivery (check Gmail inbox)
- [ ] Test SMS delivery (check phone)
- [ ] Test token expiry
- [ ] Test duplicate email/phone error handling

**Deliverables:**
- Working registration flow
- Email & phone verification
- Error handling
- **Preview link sent to you for testing**

**Estimated Hours:** 40 hours  
**Status Updates:** Daily progress reports

---

#### **Week 3: Login, JWT, Password Reset**

**User Story 1.2:** User Login & Logout

**Backend Tasks:**
- [ ] Install @nestjs/jwt and @nestjs/passport
- [ ] Create JWT strategy (Passport)
- [ ] Implement `POST /api/v1/auth/login`:
  - Accept email OR phone
  - Validate password
  - Check email/phone verified
  - Check user status (not suspended)
  - Generate JWT (7-day expiry)
  - Return user data + token
- [ ] Create `JwtAuthGuard`
- [ ] Implement `POST /api/v1/auth/logout`:
  - Add token to Redis blacklist
  - TTL = token remaining time
- [ ] Implement `GET /api/v1/users/me` (protected route)
- [ ] Password reset flow:
  - `POST /api/v1/auth/forgot-password` (send email)
  - `POST /api/v1/auth/reset-password` (verify token + update)
- [ ] Activity logging (login events)

**Frontend Tasks:**
- [ ] Create `/login` page
- [ ] Login form (email/phone + password)
- [ ] "Remember me" checkbox (localStorage)
- [ ] JWT storage (httpOnly cookie via API)
- [ ] Create auth context (React Context + Zustand)
- [ ] Implement `useAuth` hook
- [ ] Protected routes (redirect to /login if not authenticated)
- [ ] "Forgot password" link
- [ ] Create `/forgot-password` page
- [ ] Create `/reset-password` page (token from URL)
- [ ] Logout button (header)
- [ ] Auto-refresh token (before expiry)

**Testing:**
- [ ] Unit tests: Login validation
- [ ] Integration tests: Login flow
- [ ] E2E test: Login → Access protected route → Logout
- [ ] Test "Remember me" persistence
- [ ] Test password reset flow
- [ ] Test token expiry handling
- [ ] Test concurrent sessions

**Deliverables:**
- Working login/logout
- JWT authentication
- Password reset flow
- **Preview link sent to you for testing**

**Estimated Hours:** 35 hours

---

### EPIC 2: Profile Creation & Onboarding (Weeks 4-5)

#### **Week 4: Onboarding Wizard (Steps 1-2)**

**User Story 2.1:** Guided Onboarding

**Backend Tasks:**
- [ ] Create `ProfilesModule`
- [ ] Implement `POST /api/v1/profiles`:
  - Create profile linked to user
  - Validate age (male ≥21, female ≥18) - hard block
  - Calculate age from DOB
  - Calculate completeness score (0-100%)
  - Return profile data
- [ ] Implement `PATCH /api/v1/profiles/me`:
  - Update profile fields
  - Recalculate completeness
- [ ] Implement `GET /api/v1/profiles/me`
- [ ] Create DTOs with validation:
  - `CreateProfileStep1Dto` (Basic Info)
  - `CreateProfileStep2Dto` (Career & Education)
- [ ] Age validation logic (backend hard block)
- [ ] Religion/Community dropdown data:
  - `GET /api/v1/religions` (list all)
  - `GET /api/v1/religions/:id/communities` (filtered)

**Frontend Tasks:**
- [ ] Create `/profile/create` page (multi-step wizard)
- [ ] Implement stepper UI (shadcn/ui Steps component)
- [ ] **Step 1: Basic Info**
  - Fields: DOB, Marital Status, Religion (dropdown), Community (dynamic dropdown)
  - Religion selection → fetch communities → populate Community dropdown
  - Age calculation (client-side, realtime feedback)
  - Age validation (show error if <21 male or <18 female)
  - Frontend hard block: Disable "Next" button if age invalid
  - Error message: "You must be at least [21/18] years old to register"
- [ ] **Step 2: Career & Education**
  - Fields: Highest Qualification, Occupation
  - Autocomplete for common values
- [ ] Wizard state management (Zustand)
- [ ] Progress bar (% complete)
- [ ] "Save & Continue Later" button
- [ ] Navigation: Back/Next buttons
- [ ] Data persistence (auto-save drafts to backend)

**Testing:**
- [ ] Unit tests: Age validation (frontend + backend)
- [ ] Integration tests: Create profile
- [ ] E2E test: Complete Steps 1-2
- [ ] Test age hard block (21 for male, 18 for female)
- [ ] Test underage error handling
- [ ] Test religion → community cascade
- [ ] Test draft saving
- [ ] Test wizard navigation

**Deliverables:**
- Onboarding wizard (Steps 1-2)
- Age validation (hard block)
- Dynamic religion/community dropdowns
- **Preview link sent to you for testing**

**Estimated Hours:** 45 hours

---

#### **Week 5: Onboarding Wizard (Steps 3-4) + Photo Upload**

**User Story 2.1 (continued):** Photos & Physical Details

**Backend Tasks:**
- [ ] Create `PhotosModule`
- [ ] Install Cloudinary SDK
- [ ] Create `CloudinaryService`:
  - `uploadProfilePhoto(file, userId)`
  - Transformation:
    - Resize to 800x800 (main)
    - Generate 400x400 (profile view)
    - Generate 150x150 (thumbnail)
    - Add watermark: logo overlay, bottom-right, 20% opacity
  - Return URLs (original, profile, thumbnail)
- [ ] Implement `POST /api/v1/photos/upload`:
  - Accept multipart/form-data
  - Upload to Cloudinary
  - Save to database (photos table)
  - Link to profile
  - Max 5 photos per user (MVP)
  - First photo = primary by default
- [ ] Implement `DELETE /api/v1/photos/:id`
- [ ] Implement `PATCH /api/v1/photos/:id/primary`
- [ ] Implement `PATCH /api/v1/photos/reorder`

**Frontend Tasks:**
- [ ] **Step 3: Physical**
  - Fields: Height, Physical Status
  - Height picker (cm or feet/inches toggle)
- [ ] **Step 4: Photos**
  - File upload component (drag & drop or click)
  - Image preview before upload
  - Upload progress indicator
  - Photo gallery (uploaded photos)
  - Delete photo button
  - Set as primary button
  - Drag to reorder photos
  - Max 5 photos validation (frontend)
  - File size validation (max 5MB per photo)
  - File type validation (JPEG, PNG, WebP only)
  - Watermark preview (show after upload)
- [ ] Completeness score display (circular progress)
- [ ] "Complete Profile" button (Step 4)
- [ ] Success screen after completion
- [ ] Redirect to dashboard

**Testing:**
- [ ] Unit tests: Photo upload validation
- [ ] Integration tests: Upload, delete, reorder photos
- [ ] E2E test: Complete full wizard (all 4 steps)
- [ ] Test Cloudinary transformations
- [ ] Test watermark appears correctly
- [ ] Test max 5 photos limit
- [ ] Test file size/type validation
- [ ] Visual test: Verify watermark positioning

**Deliverables:**
- Complete onboarding wizard (4 steps)
- Photo upload with Cloudinary
- Watermarking (20% opacity, bottom-right)
- Completeness score calculation
- **Preview link sent to you for testing**

**Estimated Hours:** 50 hours

---

### EPIC 3: Search & Discovery (Weeks 6-8)

#### **Week 6: Basic Search**

**User Story 3.2:** Basic Search

**Backend Tasks:**
- [ ] Create `SearchModule`
- [ ] Implement `POST /api/v1/search`:
  - Accept filters: age range, height range, religion, community
  - Build Prisma query with filters
  - Apply pagination (default: 20 per page)
  - Exclude: User's own profile, suspended users, paused profiles
  - Return: Profile cards data (id, name, age, height, community, occupation, primary photo)
- [ ] Implement caching strategy (Redis):
  - Cache key: `search:{filters_hash}:page:{page}`
  - TTL: 5 minutes
  - Invalidate on profile updates
- [ ] Implement `GET /api/v1/profiles/:id`:
  - Return full profile data
  - Increment profile views counter
  - Check privacy settings (hide income/family if set)
  - Premium users: Show contact details
  - Free users: Hide contact unless mutual interest accepted

**Frontend Tasks:**
- [ ] Create `/search` page
- [ ] Search filters sidebar:
  - Age range (slider)
  - Height range (slider)
  - Religion (multi-select dropdown)
  - Community (multi-select dropdown)
  - Location (city, state)
- [ ] "Apply Filters" button
- [ ] Clear filters button
- [ ] Profile cards grid (responsive: 4 cols desktop, 2 cols tablet, 1 col mobile)
- [ ] Profile card component:
  - Primary photo (thumbnail, 150x150)
  - Name, age
  - Height, community
  - Occupation
  - "View Profile" button
  - "Send Interest" button
- [ ] Pagination controls (page numbers + next/prev)
- [ ] Loading skeleton for cards
- [ ] Empty state ("No profiles found")
- [ ] Create `/profile/[id]` page (view profile)
- [ ] Full profile display:
  - Photo gallery (carousel)
  - All profile fields
  - "Send Interest" button (if not sent already)
  - "Back to Search" button

**Testing:**
- [ ] Unit tests: Search filters validation
- [ ] Integration tests: Search with various filters
- [ ] E2E test: Apply filters → View results → View profile
- [ ] Test pagination
- [ ] Test caching (verify Redis keys)
- [ ] Test cache invalidation
- [ ] Test empty results
- [ ] Load test: Search with 1000 profiles in DB

**Deliverables:**
- Working search with filters
- Profile cards display
- Profile view page
- Pagination
- Redis caching
- **Preview link sent to you for testing**

**Estimated Hours:** 50 hours

---

#### **Week 7-8: Dashboard & Interest System**

**User Story (Dashboard):** Recommended Matches Tab

**Backend Tasks:**
- [ ] Implement `GET /api/v1/search/recommended`:
  - Calculate compatibility score (simplified for MVP):
    - Religion match: 30 points
    - Community match: 20 points
    - Age preference match: 20 points
    - Location match: 15 points
    - Education match: 15 points
  - Order by score (desc)
  - Pagination
- [ ] Implement `GET /api/v1/search/recent`:
  - Fetch recently joined profiles (last 30 days)
  - Filter by user's partner preferences
  - Order by createdAt (desc)

**User Story (Interests):** Send & Receive Interests

**Backend Tasks:**
- [ ] Create `InterestsModule`
- [ ] Implement `POST /api/v1/interests`:
  - Create interest record
  - Status: SENT
  - Optional message (max 500 chars)
  - Prevent duplicate interests
  - Queue notification email to receiver
- [ ] Implement `GET /api/v1/interests/sent`:
  - List user's sent interests
  - Include receiver profile data
  - Pagination
- [ ] Implement `GET /api/v1/interests/received`:
  - List user's received interests
  - Include sender profile data
  - Filter: SENT (pending), ACCEPTED, DECLINED
  - Pagination
- [ ] Implement `PATCH /api/v1/interests/:id/accept`:
  - Update status: ACCEPTED
  - Unlock chat between users (if free users)
  - Queue notification email to sender
- [ ] Implement `PATCH /api/v1/interests/:id/decline`:
  - Update status: DECLINED
  - Optional decline message
  - Queue notification email
- [ ] Implement `DELETE /api/v1/interests/:id` (withdraw sent interest)

**Frontend Tasks:**
- [ ] Create `/dashboard` page
- [ ] Dashboard layout:
  - Tabs: Recommended, Recent, Interests
  - Stats cards: Profile views, Interests sent/received
- [ ] **Recommended tab:**
  - Profile cards with compatibility score badge
  - "View Profile" + "Send Interest" buttons
- [ ] **Recent tab:**
  - Recently joined profiles
- [ ] **Interests tab:**
  - Sub-tabs: Sent, Received
  - Sent: List with status badges (Sent, Accepted, Declined)
  - Received: List with Accept/Decline buttons
- [ ] Create `/interests/sent` page
- [ ] Create `/interests/received` page
- [ ] Interest card component:
  - Profile photo
  - Name, age, community
  - Interest message
  - Status badge
  - Action buttons (Accept/Decline or View Profile)
- [ ] "Send Interest" modal:
  - Optional message textarea (max 500 chars)
  - Send button
  - Success toast
- [ ] "Accept Interest" confirmation modal
- [ ] "Decline Interest" modal (optional message)
- [ ] Real-time updates (when interest status changes)

**Testing:**
- [ ] Unit tests: Compatibility score calculation
- [ ] Integration tests: Send interest flow
- [ ] E2E test: Send interest → Receive → Accept → Chat unlocked
- [ ] Test duplicate interest prevention
- [ ] Test interest withdrawal
- [ ] Test email notifications
- [ ] Test dashboard stats accuracy

**Deliverables:**
- Dashboard with tabs
- Recommended matches (with compatibility scoring)
- Interest system (send/receive/accept/decline)
- Email notifications
- **Preview link sent to you for testing**

**Estimated Hours:** 60 hours (2 weeks)

---

### EPIC 4: Premium Plans & Payments (Weeks 9-11)

#### **Week 9-10: Premium Features & PhonePe Integration**

**User Story 5.1:** Premium Subscription Model

**Backend Tasks:**
- [ ] Create `PaymentsModule`
- [ ] Define premium plans (in code constants):
  ```typescript
  PLANS = {
    ONE_MONTH: { price: 1000, contacts: 100, dailyLimit: 10 },
    THREE_MONTHS: { price: 2000, contacts: 250, dailyLimit: 15 },
    ONE_YEAR: { price: 3000, contacts: 500, dailyLimit: 20 },
    INTRO_OFFER: { price: 1000, contacts: 250, dailyLimit: 15, expiry: 7 days }
  }
  ```
- [ ] Implement `GET /api/v1/payments/plans`:
  - Return all plans
  - Check if user eligible for intro offer (created < 7 days ago, never premium)
- [ ] Install PhonePe SDK
- [ ] Create `PhonePeService`:
  - `createPaymentOrder(userId, planType, amount)`
  - Generate merchantTransactionId (UUID)
  - Call PhonePe API: `/pg/v1/pay`
  - Return payment URL
- [ ] Implement `POST /api/v1/payments/create-order`:
  - Validate user not already premium (or expired)
  - Create payment record (status: PENDING)
  - Call PhonePe API
  - Return payment URL to frontend
- [ ] Implement webhook: `POST /webhooks/phonepe`:
  - Verify PhonePe signature (security)
  - Find payment record by merchantTransactionId
  - Update payment status
  - If SUCCESS:
    - Update user: role = PREMIUM, premiumExpiry, plan limits
    - Queue confirmation email
  - Return 200 OK
- [ ] Implement `GET /api/v1/payments/status/:txnId`:
  - Poll payment status (frontend polling)
- [ ] Create `PremiumGuard` (NestJS guard):
  - Check user.role === PREMIUM
  - Check premiumExpiry > now
  - Return 403 if not premium

**Frontend Tasks:**
- [ ] Create `/premium` page
- [ ] Plan comparison table:
  - Feature list comparison
  - Pricing cards
  - Highlight recommended plan (3 months)
  - Show intro offer banner (if eligible)
- [ ] "Upgrade Now" button for each plan
- [ ] Payment flow:
  - Click "Upgrade" → Call `/payments/create-order`
  - Redirect to PhonePe payment page
  - User completes payment
  - Redirect to `/payment/callback?txnId=xxx`
- [ ] Create `/payment/callback` page:
  - Poll `/payments/status/:txnId` (every 2 seconds, max 30 seconds)
  - Show loading spinner
  - On SUCCESS: Show success screen, redirect to /dashboard
  - On FAILED: Show error screen, "Retry Payment" button
- [ ] Add premium badge to user avatar (header)
- [ ] Show premium features in UI (unlocked features highlighted)

**Testing:**
- [ ] Unit tests: Plan eligibility logic
- [ ] Integration tests: Payment creation
- [ ] E2E test: Full payment flow (use PhonePe sandbox)
- [ ] Test webhook signature verification
- [ ] Test payment success scenario
- [ ] Test payment failure scenario
- [ ] Test intro offer eligibility
- [ ] Test premium expiry handling

**Deliverables:**
- Premium plans page
- PhonePe payment integration
- Webhook handling
- Premium badge
- **Preview link sent to you for testing (sandbox mode)**

**Estimated Hours:** 60 hours (2 weeks)

---

#### **Week 11: Premium User Features**

**User Story 5.3:** Direct Messaging for Premium Users

**Backend Tasks:**
- [ ] Create `MessagesModule`
- [ ] Implement `MessagesGateway` (WebSocket):
  - On connection: Authenticate JWT
  - Store userId → socketId mapping in Redis
  - Join user's room: `user:${userId}`
- [ ] WebSocket events:
  - `sendMessage`: { receiverId, content }
    - Validate premium status OR mutual interest accepted
    - Check daily contact limit (premium users)
    - Save message to database
    - Emit to receiver: `newMessage`
    - Update unread count in Redis
  - `typing`: { receiverId }
    - Emit to receiver: `userTyping`
  - `stopTyping`: { receiverId }
    - Emit to receiver: `userStoppedTyping`
  - `messageRead`: { messageId }
    - Update message.isRead = true
    - Emit to sender: `messageRead`
- [ ] Implement `GET /api/v1/messages/conversations`:
  - List all conversations (distinct users chatted with)
  - Include last message, unread count
  - Order by last message time (desc)
- [ ] Implement `GET /api/v1/messages/:userId`:
  - Get chat history with specific user
  - Pagination (load older messages)
  - Mark as read on load
- [ ] Implement `POST /api/v1/messages` (REST fallback for offline):
  - Save message
  - Queue notification if receiver offline
- [ ] Daily contact limit tracking:
  - Increment contactsToday on first message to new user
  - Reset counter daily (cron job or check lastContactDate)

**Frontend Tasks:**
- [ ] Create `/messages` page
- [ ] Chat list (left sidebar):
  - List of conversations
  - Profile photo, name
  - Last message preview
  - Unread badge (count)
  - Timestamp
  - Click → Open chat
- [ ] Chat window (right panel):
  - Message bubbles (sent: right, received: left)
  - Timestamps
  - Message status: Sent, Delivered, Read (checkmarks)
  - Typing indicator: "User is typing..."
  - Message input (textarea)
  - Send button
  - Scroll to bottom on new message
  - Load more messages on scroll up
- [ ] Socket.IO connection:
  - Connect on mount
  - Authenticate with JWT
  - Listen to events
  - Emit typing events (debounced)
- [ ] "Send Message" button on profiles (premium users):
  - Replace "Send Interest" button
  - Opens chat window
- [ ] Free users: Chat unlocked after mutual interest acceptance
- [ ] Premium daily limit UI:
  - Show "X contacts remaining today" in header
  - Disable "Send Message" if limit reached
  - Show upgrade prompt

**Testing:**
- [ ] Unit tests: Message validation
- [ ] Integration tests: WebSocket events
- [ ] E2E test: Send message → Receive → Reply
- [ ] Test typing indicators
- [ ] Test read receipts
- [ ] Test offline message delivery (email notification)
- [ ] Test daily contact limit
- [ ] Test premium vs free user permissions
- [ ] Load test: 100 concurrent WebSocket connections

**Deliverables:**
- Real-time chat (WebSocket)
- Chat UI (conversation list + chat window)
- Typing indicators
- Read receipts
- Daily contact limits
- **Preview link sent to you for testing**

**Estimated Hours:** 55 hours

---

### EPIC 5: Admin Dashboard (Weeks 12-14)

#### **Week 12: Admin Authentication & User Management**

**User Story 6.1:** Basic Admin Dashboard

**Backend Tasks:**
- [ ] Create `AdminModule`
- [ ] Create `AdminGuard` (checks role = ADMIN or SUPER_ADMIN)
- [ ] Implement `POST /api/v1/admin/login`:
  - Separate login for admin users
  - Return admin JWT (longer expiry, different secret)
- [ ] Implement `GET /api/v1/admin/users`:
  - Search users by: email, name, user ID
  - Filter by: status, role, registration date
  - Pagination
  - Return user + profile data
- [ ] Implement `GET /api/v1/admin/users/:id`:
  - Detailed user view
  - Profile data
  - Activity logs
  - Payment history
  - Reports (if any)
- [ ] Implement `PATCH /api/v1/admin/users/:id/status`:
  - Change user status: ACTIVE, SUSPENDED, DEACTIVATED
  - Log action in activity_logs
- [ ] Implement `DELETE /api/v1/admin/users/:id` (SUPER_ADMIN only):
  - Soft delete (status = DELETED)
  - Cascade: Hide profile, delete photos, anonymize data
- [ ] Implement `GET /api/v1/admin/stats`:
  - Total users, active users, premium users
  - Registrations (last 7 days, last 30 days)
  - Revenue (last month)
  - Top communities

**Frontend Tasks:**
- [ ] Create `/admin` layout
- [ ] Admin login page: `/admin/login`
- [ ] Admin sidebar navigation:
  - Dashboard (stats)
  - Users
  - Portals (Religions, Communities)
  - Success Stories
  - Reports
  - Settings
- [ ] Create `/admin/dashboard` (stats overview)
- [ ] Dashboard cards:
  - Total users
  - Active users
  - Premium users
  - Revenue (last 30 days)
- [ ] Charts:
  - Registrations over time (line chart)
  - Users by community (pie chart)
- [ ] Create `/admin/users` page
- [ ] User search:
  - Search input (email, name, ID)
  - Filter dropdowns (status, role)
  - Date range picker (registration date)
- [ ] Users table:
  - Columns: ID, Name, Email, Phone, Status, Role, Registered Date
  - Actions: View, Edit Status, Delete
  - Pagination
- [ ] Create `/admin/users/[id]` page (user details)
- [ ] User details view:
  - User info card
  - Profile info card
  - Activity timeline
  - Payment history table
  - Reports against user (if any)
- [ ] "Change Status" button (modal with dropdown)
- [ ] "Delete User" button (confirmation modal, SUPER_ADMIN only)

**Testing:**
- [ ] Unit tests: Admin guard
- [ ] Integration tests: User search
- [ ] E2E test: Admin login → Search user → Change status
- [ ] Test admin permissions (ADMIN vs SUPER_ADMIN)
- [ ] Test user deletion (soft delete)
- [ ] Test activity logging

**Deliverables:**
- Admin login
- Admin dashboard with stats
- User search & management
- Status change functionality
- **Preview link sent to you for testing**

**Estimated Hours:** 50 hours

---

#### **Week 13: Portal Management (Religions & Communities)**

**User Story 11.4:** Religion Management Module  
**User Story 11.5:** Community Management Module

**Backend Tasks:**
- [ ] Implement `POST /api/v1/admin/religions`:
  - Create religion portal
  - Fields: name, slug, heroTitle, heroDescription, heroImageUrl, seoTitle, seoDescription, status
  - Upload hero image to Cloudinary
- [ ] Implement `PATCH /api/v1/admin/religions/:id`:
  - Update religion portal
  - Regenerate slug if name changed (prevent breaking existing URLs)
- [ ] Implement `DELETE /api/v1/admin/religions/:id`:
  - Soft delete (status = INACTIVE)
  - Prevent deletion if communities linked
- [ ] Implement `POST /api/v1/admin/communities`:
  - Create community portal
  - Fields: name, slug, religionId, heroTitle, heroDescription, heroImageUrl, about, traditions, seoTitle, seoDescription, status
  - Upload hero image to Cloudinary
- [ ] Implement `PATCH /api/v1/admin/communities/:id`:
  - Update community portal
- [ ] Implement `DELETE /api/v1/admin/communities/:id`:
  - Soft delete
  - Prevent deletion if profiles linked

**Frontend Tasks:**
- [ ] Create `/admin/portals/religions` page
- [ ] Religions table:
  - Columns: Name, Slug, Status, Communities Count, Actions
  - "Add New Religion" button
- [ ] Create `/admin/portals/religions/create` page
- [ ] Create religion form:
  - Name input
  - Slug (auto-generated from name, editable)
  - Hero title, description
  - Hero image upload (Cloudinary widget)
  - SEO title, description
  - Status toggle (Active/Inactive)
  - Submit button
- [ ] Create `/admin/portals/religions/[id]/edit` page (same form, pre-filled)
- [ ] Create `/admin/portals/communities` page
- [ ] Communities table:
  - Columns: Name, Slug, Religion, Status, Profiles Count, Actions
  - Filter by religion dropdown
  - "Add New Community" button
- [ ] Create `/admin/portals/communities/create` page
- [ ] Create community form:
  - Name, slug
  - Parent religion (dropdown)
  - Hero title, description, image
  - About, traditions (rich text editor)
  - SEO fields
  - Status toggle
  - Submit button
- [ ] Create `/admin/portals/communities/[id]/edit` page
- [ ] Image upload component:
  - Cloudinary upload widget integration
  - Image preview
  - Delete image button

**Testing:**
- [ ] Unit tests: Slug generation
- [ ] Integration tests: Create/update portal
- [ ] E2E test: Create religion → Create community under it → View on frontend
- [ ] Test image upload to Cloudinary
- [ ] Test delete prevention (if linked entities exist)
- [ ] Test slug uniqueness validation

**Deliverables:**
- Religion portal management
- Community portal management
- Cloudinary integration for hero images
- **Preview link sent to you for testing**

**Estimated Hours:** 45 hours

---

#### **Week 14: Success Stories CMS & Reports**

**Success Stories CMS**

**Backend Tasks:**
- [ ] Create `StoriesModule`
- [ ] Implement `POST /api/v1/admin/stories`:
  - Create success story
  - Fields: groomName, brideName, marriageDate, title, story, featuredImage, galleryImages[], communityId, isPublished
  - Generate slug from title
  - Upload images to Cloudinary
- [ ] Implement `PATCH /api/v1/admin/stories/:id`:
  - Update story
- [ ] Implement `DELETE /api/v1/admin/stories/:id`:
  - Delete story (hard delete)
- [ ] Implement `PATCH /api/v1/admin/stories/:id/publish`:
  - Publish story (isPublished = true, publishedAt = now)
- [ ] Implement `GET /api/v1/stories` (public):
  - List published stories
  - Filter by community
  - Pagination
- [ ] Implement `GET /api/v1/stories/:slug` (public):
  - Get single story
  - Increment views counter

**Reports Module**

**Backend Tasks:**
- [ ] Create `ReportsModule`
- [ ] Implement `POST /api/v1/reports`:
  - Create report
  - Fields: reportedUserId, reason, description
  - Status: PENDING
- [ ] Implement `GET /api/v1/admin/reports`:
  - List all reports
  - Filter by status (PENDING, REVIEWED, ACTIONED, DISMISSED)
  - Pagination
- [ ] Implement `PATCH /api/v1/admin/reports/:id/review`:
  - Update status: REVIEWED
  - Add reviewNotes, actionTaken
  - If action = suspend user, call user status update

**Frontend Tasks:**
- [ ] Create `/admin/stories` page
- [ ] Stories table:
  - Columns: Title, Couple, Community, Status (Draft/Published), Views, Actions
  - "Add New Story" button
- [ ] Create `/admin/stories/create` page
- [ ] Create story form:
  - Groom name, bride name
  - Marriage date (date picker)
  - Title (auto-generate slug)
  - Story (rich text editor: TipTap or similar)
  - Featured image upload
  - Gallery images (multi-upload, drag to reorder)
  - Community (dropdown)
  - "Save as Draft" button
  - "Publish" button
- [ ] Create `/admin/stories/[id]/edit` page
- [ ] Create `/stories` page (public, user-facing)
- [ ] Stories grid:
  - Featured image
  - Couple names
  - Title
  - Date
  - Read more link
- [ ] Create `/stories/[slug]` page (single story)
- [ ] Story detail view:
  - Hero image
  - Couple names, date
  - Story content (formatted)
  - Image gallery (lightbox)
  - Related stories (same community)
- [ ] Create `/admin/reports` page
- [ ] Reports table:
  - Columns: Reported User, Reporter, Reason, Status, Date, Actions
  - Filter by status
- [ ] Create report detail modal:
  - User profiles (reporter + reported)
  - Reason, description
  - Review form:
    - Status dropdown (REVIEWED, ACTIONED, DISMISSED)
    - Action taken dropdown (Suspend user, Warn, No action)
    - Review notes (textarea)
    - Submit button
- [ ] "Report User" button on profiles (user-facing):
  - Opens report modal
  - Reason dropdown (Fake profile, Inappropriate, Spam, Other)
  - Description textarea
  - Submit button

**Testing:**
- [ ] Unit tests: Slug generation
- [ ] Integration tests: Create/publish story
- [ ] E2E test: Create story → Publish → View on frontend
- [ ] Test rich text editor (formatting preserved)
- [ ] Test image gallery upload
- [ ] Test report creation and review flow
- [ ] Test report-based user suspension

**Deliverables:**
- Success stories CMS (admin)
- Published stories page (public)
- Single story page (public)
- Report system (user-facing + admin review)
- **Preview link sent to you for testing**

**Estimated Hours:** 50 hours

---

### EPIC 6: Community Portals & WhatsApp (Weeks 15-16)

#### **Week 15: Religion & Community Sub-Portals (SEO)**

**User Story 11.1:** Religion Portal Pages  
**User Story 11.2:** Community Landing Pages

**Backend Tasks:**
- [ ] Implement `GET /api/v1/portals/religions/:slug`:
  - Fetch religion data (hero content, SEO)
  - Fetch communities under this religion
  - Return data
- [ ] Implement `GET /api/v1/portals/communities/:religionSlug/:communitySlug`:
  - Fetch community data (hero content, SEO, about, traditions)
  - Fetch success stories linked to this community
  - Return data
- [ ] Pre-filter search by portal:
  - `/api/v1/search?religion=hindu` → filter profiles by religion
  - `/api/v1/search?community=bunt` → filter profiles by community

**Frontend Tasks:**
- [ ] Create `/[religion]/page.tsx` (dynamic route)
- [ ] Religion portal page:
  - Hero section:
    - Background image (from admin)
    - Title, description (from admin)
  - Communities grid:
    - List all communities under this religion
    - Click → Navigate to community portal
  - Profile search (pre-filtered by religion):
    - Show profiles from ALL communities in this religion
    - Same search UI as main search
  - Success stories section:
    - Show stories from any community in this religion
    - Carousel or grid
  - SEO:
    - Dynamic meta tags (title, description from admin)
    - Structured data (schema.org/Organization)
- [ ] Create `/[religion]/[community]/page.tsx` (nested dynamic route)
- [ ] Community portal page:
  - Hero section (community-specific)
  - About section (from admin: about, traditions)
  - Profile search (pre-filtered by community):
    - Only profiles from THIS community
  - Success stories (community-specific)
  - SEO:
    - Meta tags
    - Breadcrumbs: Home > Religion > Community
    - Structured data
- [ ] Homepage updates:
  - Add "Explore Communities" section
  - Grid of religion cards (Hindu, Christian, Muslim)
  - Click → Navigate to religion portal

**Testing:**
- [ ] Unit tests: Dynamic route params
- [ ] E2E test: Navigate Home → Religion → Community → View profiles
- [ ] SEO test: Verify meta tags generated correctly
- [ ] Test pre-filtered search (only community profiles shown)
- [ ] Test 404 for invalid slugs
- [ ] Lighthouse SEO audit (target: 90+)

**Deliverables:**
- Religion portals (e.g., /hindu)
- Community portals (e.g., /hindu/bunt)
- Pre-filtered search on portals
- SEO optimization (meta tags, structured data)
- **Preview link sent to you for testing**

**Estimated Hours:** 45 hours

---

#### **Week 16: WhatsApp Integration, Final Polish & MVP Launch**

**WhatsApp Integration**

**Backend Tasks:**
- [ ] Add WhatsApp number to environment variables
- [ ] Create WhatsApp link generator utility:
  ```typescript
  generateWhatsAppLink(message = "Hello, I need support") {
    return `https://wa.me/${WHATSAPP_NUMBER}?text=${encodeURIComponent(message)}`
  }
  ```

**Frontend Tasks:**
- [ ] Create `WhatsAppButton` component:
  - Floating button (bottom-right corner)
  - WhatsApp icon (green)
  - Click → Opens WhatsApp chat with support number
  - Pre-filled message: "Hello, I need support with Kudla Matrimony"
- [ ] Add component to root layout (appears on all pages)
- [ ] Add to `/contact` page (static contact form):
  - Name, email, subject, message fields
  - "Or chat with us on WhatsApp" button

**Final Polish Tasks:**

**Homepage:**
- [ ] Hero section:
  - Headline: "Find Your Perfect Match in the Kudla Community"
  - Search quick filters (religion, community)
  - CTA: "Get Started" button → /register
- [ ] Features section (icons + descriptions):
  - Verified Profiles
  - Advanced Search
  - Secure & Private
  - 24/7 Support
- [ ] Communities section (religion cards)
- [ ] Success stories section (carousel)
- [ ] Testimonials
- [ ] Footer:
  - Links: About, Contact, Privacy Policy, Terms of Service
  - Social media links
  - Copyright

**UX Improvements:**
- [ ] Add loading states (skeletons) to all pages
- [ ] Add error boundaries (catch React errors)
- [ ] Add toasts for all success/error actions
- [ ] Add confirmation modals for destructive actions
- [ ] Optimize images (lazy loading, Next.js Image)
- [ ] Add animations (Framer Motion or CSS transitions)
- [ ] Mobile responsiveness audit (test on all screen sizes)
- [ ] Accessibility audit:
  - Keyboard navigation
  - Screen reader compatibility
  - Alt text for all images
  - ARIA labels

**Documentation:**
- [ ] Create Terms of Service page
- [ ] Create Privacy Policy page (template provided by me)
- [ ] Create FAQ page
- [ ] Create "How It Works" page

**Pre-Launch Testing:**
- [ ] Full regression testing (all features)
- [ ] Cross-browser testing (Chrome, Firefox, Safari, Edge)
- [ ] Mobile testing (iOS Safari, Android Chrome)
- [ ] Performance audit (Lighthouse: 90+ all metrics)
- [ ] Security audit:
  - SQL injection testing
  - XSS testing
  - CSRF testing
  - Rate limiting testing
- [ ] Load testing (simulate 1000 concurrent users)

**Launch Preparation:**
- [ ] Set up production environment variables
- [ ] Configure production database (backup strategy)
- [ ] Set up monitoring alerts (Sentry, Better Stack)
- [ ] Create admin user (you)
- [ ] Seed production database (religions, communities)
- [ ] DNS final configuration
- [ ] SSL certificate verification
- [ ] Create launch checklist

**MVP LAUNCH (End of Week 16):**
- [ ] Deploy to production
- [ ] Smoke testing on production
- [ ] Send you launch notification
- [ ] Provide admin credentials
- [ ] Provide monitoring dashboard links
- [ ] **🎉 KUDLA MATRIMONY IS LIVE! 🎉**

**Deliverables:**
- WhatsApp support integration
- Polished homepage
- Legal pages (Terms, Privacy)
- FAQ page
- Full testing suite passed
- **PRODUCTION LAUNCH ✅**

**Estimated Hours:** 55 hours

---

## WEEK-BY-WEEK SUMMARY

| Week | Epic | Deliverables | Hours | Your Testing |
|------|------|--------------|-------|--------------|
| **1** | Setup | Infrastructure, deployments, admin access | 40 | Admin login |
| **2** | Auth | Registration, email/phone verification | 40 | Register flow |
| **3** | Auth | Login, JWT, password reset | 35 | Login flow |
| **4** | Profile | Onboarding wizard (Steps 1-2) | 45 | Wizard Steps 1-2 |
| **5** | Profile | Onboarding wizard (Steps 3-4), photos | 50 | Complete wizard |
| **6** | Search | Basic search with filters | 50 | Search profiles |
| **7-8** | Search | Dashboard, interests | 60 | Send/receive interests |
| **9-10** | Premium | Plans, PhonePe integration | 60 | Payment flow (sandbox) |
| **11** | Premium | Direct messaging (WebSocket) | 55 | Chat functionality |
| **12** | Admin | User management | 50 | Admin dashboard |
| **13** | Admin | Portal management | 45 | Create portals |
| **14** | Admin | Success stories, reports | 50 | CMS + reports |
| **15** | Portals | Religion/community SEO portals | 45 | /hindu/bunt pages |
| **16** | Launch | WhatsApp, polish, launch | 55 | Full app testing |

**Total Hours:** 680 hours  
**Total Weeks:** 16 weeks  
**Average:** 42.5 hours/week  

---

## 4. PHASE 2: ENHANCEMENTS (Weeks 17-24)

**Duration:** 8 weeks  
**Goal:** Advanced features for better matchmaking  

### Features to Build:

**Weeks 17-18: Advanced Matching Algorithm**
- Implement full compatibility scoring (40% preferences, 30% basic, 20% lifestyle, 10% family)
- Partner preference matching logic
- "Two-Way Matches" tab (mutual preference match)
- "Seeking You" tab (profiles that match YOUR details)

**Weeks 19-20: Horoscope Matching**
- Add astrology fields to profile (Phase 2 fields from schema)
- Horoscope image upload
- Manglik matching logic
- Birth chart compatibility (basic: Manglik Yes/No filter)

**Weeks 21-22: Saved Searches & Notifications**
- Save search criteria
- Email digests (daily/weekly)
- Match alerts (when new profiles match your preferences)
- Interest received notifications (push + email)

**Weeks 23-24: Advanced Profile Features**
- Rich text bio editor (TipTap)
- Video/Audio intro upload (Cloudinary video)
- Family details section
- Lifestyle section (diet, smoking, drinking)
- Expand partner preferences (all fields)

**Estimated Hours:** 320 hours (8 weeks × 40 hours)

---

## 5. PHASE 3: SCALE & GROWTH (Month 7+)

**Duration:** Ongoing  
**Goal:** Growth features, mobile apps, optimization  

### Features to Build:

**Months 7-8: Mobile Apps**
- React Native app (iOS + Android)
- All MVP features in mobile app
- Push notifications
- App Store + Play Store deployment

**Months 9-10: Advanced Features**
- Video calls (Twilio/Agora integration)
- Verified profiles (ID verification)
- Profile boost (paid feature: appear in top search)
- Priority customer support for premium users

**Months 11-12: Analytics & Optimization**
- Advanced admin analytics dashboard
- User behavior tracking
- A/B testing framework
- Performance optimization
- Database query optimization
- CDN optimization (image delivery)

**Ongoing:**
- Bug fixes
- Feature requests
- Performance monitoring
- Security updates
- Scaling infrastructure

---

## 6. DEPENDENCIES MAP

### Critical Path

```
Week 1 (Setup) → BLOCKS ALL
   ↓
Week 2-3 (Auth) → BLOCKS Profiles, Search, Premium, Admin
   ↓
Week 4-5 (Profiles) → BLOCKS Search, Interests
   ↓
Week 6 (Search) → BLOCKS Interests
   ↓
Week 7-8 (Interests) → BLOCKS Premium (Chat unlock)
   ↓
Week 9-11 (Premium) → BLOCKS Chat
   ↓
Week 12-14 (Admin) → INDEPENDENT (can be parallel)
   ↓
Week 15-16 (Portals + Launch) → REQUIRES ALL
```

### Parallel Work Opportunities

| Can Build in Parallel | Weeks |
|------------------------|-------|
| Admin Dashboard | 12-14 (while Chat is being built) |
| Success Stories CMS | 14 (independent feature) |
| Community Portals | 15 (independent of Chat/Premium) |

---

## 7. RISK MANAGEMENT

### Identified Risks

| Risk | Probability | Impact | Mitigation |
|------|------------|--------|------------|
| **PhonePe sandbox issues** | Medium | High | Test early, have backup payment gateway (Razorpay) |
| **Cloudinary quota exceeded** | Low | Medium | Monitor usage, upgrade plan if needed |
| **WebSocket scaling issues** | Low | High | Use Redis adapter for Socket.IO (multi-instance support) |
| **Database connection limits** | Medium | High | Use Neon connection pooling, upgrade to Pro if needed |
| **Third-party API downtime** | Low | Medium | Implement retry logic, queue failed jobs |

### Mitigation Strategies

**For each risk:**
1. Early detection: Monitor services daily
2. Backup plan: Alternative services configured
3. Communication: Notify you immediately if critical issue
4. Rollback: Keep previous version deployable

---

## 🎯 NEXT STEPS

**Immediate Action (You):**
1. Review this roadmap
2. Approve timeline
3. Provide API keys (from 00-SETUP-GUIDE.md)
4. Create service accounts

**Immediate Action (Me):**
1. Week 1 starts as soon as you're ready
2. Daily updates begin
3. First preview link by Day 6 (Week 1)

---

**Let's build Kudla Matrimony!** 🚀

**Questions? Ask me anytime during development.**
