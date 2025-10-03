# 📅 KUDLA MATRIMONY - UPDATED PHASED ROADMAP (v2.0)

**Version:** 2.0 (Updated after Shaadi.com analysis)  
**Date:** October 3, 2025  
**Timeline:** 19 weeks to MVP Launch (was 16 weeks)  
**Total Features:** 53 features (was 42)  
**Feature Parity with Shaadi.com:** 82%  

---

## 🆕 WHAT'S NEW IN VERSION 2.0

### **11 Critical Features Added:**

1. ✅ **Family Details** (Week 5) - Father, mother, siblings info
2. ✅ **Lifestyle Fields** (Week 5) - Diet, smoking, drinking
3. ✅ **Advanced Search Filters** (Week 6) - More filter options
4. ✅ **Shortlist/Favorites** (Week 8) - Save profiles for later
5. ✅ **Block/Ignore Users** (Week 8) - Privacy control
6. ✅ **Saved Searches** (Week 8) - Save & rerun searches
7. ✅ **Profile Boost** (Week 10) - Paid feature to appear at top
8. ✅ **Photo Sharing in Chat** (Week 11) - Send images in messages
9. ✅ **File Attachments** (Week 11) - Share PDFs (horoscope, etc.)
10. ✅ **Who Viewed My Profile** (Week 12) - Premium analytics
11. ✅ **Priority Support Badge** (Week 10) - Premium user indicator

### **Timeline Changes:**

| Version | Weeks | Features | Launch Date |
|---------|-------|----------|-------------|
| **v1.0 (Original)** | 16 weeks | 42 features | ~4 months |
| **v2.0 (Updated)** | 19 weeks | 53 features | ~4.75 months |
| **Difference** | +3 weeks | +11 features | +3 weeks |

---

## 📊 UPDATED PROJECT OVERVIEW

### Phase Summary

| Phase | Duration | Weeks | Features | Cost/Month |
|-------|----------|-------|----------|------------|
| **Phase 0** | Setup | Week 1 | Infrastructure | $10/mo |
| **Phase 1** | MVP | Weeks 2-19 | 53 features | $10-159/mo |
| **Phase 2** | Enhancements | Weeks 20-27 | Advanced features | $159-300/mo |
| **Phase 3** | Scale | Month 8+ | Mobile apps, growth | $300+/mo |

---

## 📋 DETAILED WEEK-BY-WEEK ROADMAP

### PHASE 0: SETUP & INFRASTRUCTURE

**Week 1: Infrastructure Setup** *(No changes from v1.0)*

Same as original plan - see previous roadmap.

---

### PHASE 1: MVP DEVELOPMENT (WEEKS 2-19)

---

## WEEK 2-3: USER AUTHENTICATION

*(No changes from v1.0 - Same as original)*

**Week 2:** Registration, Email/Phone Verification  
**Week 3:** Login, JWT, Password Reset  

**Details:** See original roadmap (unchanged)

---

## WEEK 4-5: PROFILE CREATION & ONBOARDING

### **Week 4: Onboarding Steps 1-2 (ENHANCED)**

**User Story 2.1:** Guided Onboarding Wizard

#### **Backend Tasks (Updated):**

```typescript
// All original tasks PLUS:

Step 1 DTO Enhancement:
- [ ] Add validation for family details:
  - fatherName (optional)
  - fatherOccupation (optional)
  - motherName (optional)
  - motherOccupation (optional)
  - siblings (string, e.g., "1 brother, 2 sisters")
  - familyType (enum: JOINT, NUCLEAR)
  - familyValues (enum: TRADITIONAL, MODERATE, LIBERAL)
  - familyStatus (enum: MIDDLE_CLASS, UPPER_MIDDLE, RICH)

Step 2 DTO Enhancement:
- [ ] Add lifestyle fields:
  - diet (enum: VEGETARIAN, NON_VEGETARIAN, EGGETARIAN, VEGAN)
  - smoking (enum: NO, OCCASIONALLY, REGULARLY)
  - drinking (enum: NO, SOCIALLY, REGULARLY)

- [ ] Update completeness score calculation:
  - Family details: +10%
  - Lifestyle: +5%
```

#### **Frontend Tasks (Updated):**

```typescript
// Step 1: Basic Info + Family Details
- [ ] Expand Step 1 form:
  - Basic Info section (existing)
  - NEW: Family Details section
    - Father's name, occupation (optional)
    - Mother's name, occupation (optional)
    - Siblings (text input with helper text)
    - Family type (dropdown)
    - Family values (dropdown)
    - Family status (dropdown)
  - Toggle: "I'll add this later" (skip to Step 2)

// Step 2: Career + Lifestyle
- [ ] Add Lifestyle section to Step 2:
  - Diet preference (dropdown with icons)
  - Smoking habits (dropdown)
  - Drinking habits (dropdown)
  - Visual indicators (icons for each choice)

- [ ] Update progress bar to reflect new fields
```

**Deliverables (Enhanced):**
- ✅ Onboarding Steps 1-2 complete
- ✅ Family details captured
- ✅ Lifestyle preferences captured
- ✅ Enhanced completeness score
- **Preview link sent to you for testing**

**Estimated Hours:** 50 hours (was 45)

---

### **Week 5: Onboarding Steps 3-4 + Photos** *(No changes)*

Same as original - Photo upload with Cloudinary watermarking.

**Estimated Hours:** 50 hours

---

## WEEK 6: SEARCH & DISCOVERY (ENHANCED)

### **Week 6: Advanced Search with More Filters**

**User Story 3.2 (Enhanced):** Advanced Search Functionality

#### **Backend Tasks (Updated):**

```typescript
// Original search implementation PLUS:

Advanced Filters:
- [ ] Extend search DTO with additional filters:
  - educationLevel[] (Bachelors, Masters, PhD, etc.)
  - occupation[] (Engineer, Doctor, Teacher, etc.)
  - incomeRange { min, max } (in lakhs)
  - diet[] (Vegetarian, etc.)
  - smoking[] (No, Occasionally, Regularly)
  - drinking[] (No, Socially, Regularly)
  - familyType[] (Joint, Nuclear)
  - familyValues[] (Traditional, Moderate, Liberal)
  - hasPhoto (boolean - only profiles with photos)

- [ ] Optimize database queries:
  - Add indexes for new filter fields
  - Query builder for dynamic filters
  - Ensure <100ms query time

- [ ] Implement filter combinations:
  - AND logic for multiple filters
  - OR logic within same category
  - Example: (Engineer OR Doctor) AND (Vegetarian) AND (Non-smoker)
```

#### **Frontend Tasks (Updated):**

```typescript
// Enhanced search filters UI:
- [ ] Expand filters sidebar:
  - Basic Filters (existing):
    - Age range slider
    - Height range slider
    - Religion multi-select
    - Community multi-select
  
  - NEW: Advanced Filters (collapsible):
    - Education level (multi-select)
    - Occupation (multi-select with search)
    - Income range (dual slider: 0-50L+)
    - Lifestyle filters:
      - Diet (checkboxes)
      - Smoking (checkboxes)
      - Drinking (checkboxes)
    - Family background:
      - Family type (checkboxes)
      - Family values (checkboxes)
    - Photo filter (toggle: "Only show profiles with photos")

- [ ] Filter UI/UX:
  - "Show Advanced Filters" toggle button
  - Active filters chips (removable)
  - "Clear All Filters" button
  - Filter count badge (e.g., "12 filters applied")
  - Save search button (linked to Saved Searches feature)

- [ ] Search results enhancements:
  - Show match percentage based on filters
  - Highlight matching criteria on profile cards
  - Sort options: Relevance, Recent, Compatibility
```

**Testing (Enhanced):**
- [ ] Test all filter combinations
- [ ] Test performance with 10+ filters applied
- [ ] Test filter persistence (saved in URL params)
- [ ] Test mobile responsiveness of expanded filters

**Deliverables (Enhanced):**
- ✅ Advanced search with 15+ filter options
- ✅ Filter combinations working
- ✅ Fast search results (<500ms)
- ✅ Mobile-responsive filter UI
- **Preview link sent to you for testing**

**Estimated Hours:** 60 hours (was 50)

---

## WEEK 7-8: INTERESTS + NEW FEATURES

### **Week 7: Interest System** *(Same as original)*

**Details:** Send/receive interests - unchanged from v1.0

**Estimated Hours:** 30 hours

---

### **Week 8: Dashboard + 3 NEW FEATURES**

#### **NEW FEATURE 1: Shortlist/Favorites**

**User Story:** As a user, I want to save interesting profiles to my favorites list so I can review them later.

**Backend Tasks:**

```typescript
// Database Schema:
model Favorite {
  id          String   @id @default(cuid())
  userId      String
  user        User     @relation(fields: [userId], references: [id])
  profileId   String
  profile     Profile  @relation(fields: [profileId], references: [id])
  note        String?  // Optional private note
  createdAt   DateTime @default(now())
  
  @@unique([userId, profileId])
  @@index([userId])
  @@index([createdAt])
}

// API Endpoints:
- [ ] POST /api/v1/favorites
  - Body: { profileId, note? }
  - Validation: Profile exists, not already favorited
  - Return: Created favorite

- [ ] GET /api/v1/favorites
  - Query: page, limit, sortBy
  - Return: Paginated list with profile data
  - Include: profile photos, basic info

- [ ] DELETE /api/v1/favorites/:id
  - Remove from favorites
  - Return: 204 No Content

- [ ] GET /api/v1/favorites/count
  - Return: Total favorites count
```

**Frontend Tasks:**

```typescript
- [ ] "Add to Favorites" button on profile cards:
  - Heart icon (outline when not favorited, filled when favorited)
  - Click to add/remove
  - Optimistic update (instant UI feedback)
  - Success toast: "Added to favorites" / "Removed from favorites"

- [ ] Create /favorites page:
  - Same grid layout as search results
  - Profile cards with "Remove" button
  - Optional note display
  - Empty state: "No favorites yet. Start exploring!"
  - Pagination

- [ ] Dashboard integration:
  - "Favorites" tab in dashboard
  - Favorites count badge in navigation
  - Quick access from header

- [ ] Mobile:
  - Swipe gesture to remove (optional)
  - Responsive grid
```

**Testing:**
- [ ] Add/remove favorites
- [ ] Check uniqueness constraint (can't favorite twice)
- [ ] Test pagination
- [ ] Test favorites count updates

**Estimated Hours:** 12 hours

---

#### **NEW FEATURE 2: Block/Ignore Users**

**User Story:** As a user, I want to block unwanted users so they cannot contact me or see my profile.

**Backend Tasks:**

```typescript
// Database Schema:
model BlockedUser {
  id          String   @id @default(cuid())
  blockerId   String
  blocker     User     @relation("Blocker", fields: [blockerId], references: [id])
  blockedId   String
  blocked     User     @relation("Blocked", fields: [blockedId], references: [id])
  reason      String?  // Optional reason
  createdAt   DateTime @default(now())
  
  @@unique([blockerId, blockedId])
  @@index([blockerId])
  @@index([blockedId])
}

// API Endpoints:
- [ ] POST /api/v1/blocked-users
  - Body: { userId, reason? }
  - Validation: Can't block yourself, user exists
  - Side effects:
    - Remove from favorites (if favorited)
    - Delete all interests between users
    - Hide profile from each other's searches
  - Return: Created block record

- [ ] GET /api/v1/blocked-users
  - Return: List of blocked users (minimal info: id, name)
  - Pagination

- [ ] DELETE /api/v1/blocked-users/:id (Unblock)
  - Remove block
  - Return: 204 No Content

// Integration:
- [ ] Update search query:
  - WHERE profile.userId NOT IN (blockedByMe OR blockedMe)

- [ ] Update profile view:
  - Return 403 if user is blocked

- [ ] Update chat:
  - Prevent messages if blocked
  - Hide existing conversations
```

**Frontend Tasks:**

```typescript
- [ ] "Block User" button on profile page:
  - Location: Three-dot menu (⋮) on profile
  - Confirmation modal: "Are you sure you want to block [Name]?"
  - Optional: Reason dropdown (Inappropriate, Fake, Spam, Other)
  - On confirm: Block and redirect to search

- [ ] Create /settings/blocked-users page:
  - List of blocked users
  - "Unblock" button for each
  - Empty state: "No blocked users"

- [ ] Block indicators:
  - Blocked users hidden from search
  - If somehow accessed: "This profile is unavailable"
  - Chat disabled with blocked users

- [ ] Report integration:
  - "Report & Block" option (combines reporting + blocking)
```

**Testing:**
- [ ] Block user → Verify hidden from search
- [ ] Block user → Verify can't send interest
- [ ] Block user → Verify chat disabled
- [ ] Unblock → Verify user reappears
- [ ] Test mutual block scenario

**Estimated Hours:** 14 hours

---

#### **NEW FEATURE 3: Saved Searches**

**User Story:** As a user, I want to save my search criteria so I can quickly rerun my favorite searches.

**Backend Tasks:**

```typescript
// Database Schema:
model SavedSearch {
  id          String   @id @default(cuid())
  userId      String
  user        User     @relation(fields: [userId], references: [id])
  name        String   // User-provided name: "Doctors in Bangalore"
  filters     Json     // Store entire filter object
  createdAt   DateTime @default(now())
  lastUsedAt  DateTime?
  
  @@index([userId])
  @@index([createdAt])
}

// API Endpoints:
- [ ] POST /api/v1/searches/save
  - Body: { name, filters: { ageRange, community, ... } }
  - Validation: Name required, filters object valid
  - Max: 10 saved searches per user (prevent spam)
  - Return: Created saved search

- [ ] GET /api/v1/searches/saved
  - Return: List of user's saved searches
  - Include: name, filter summary (e.g., "Age 25-30, Bunt")
  - Order by: lastUsedAt DESC (most recent first)

- [ ] PUT /api/v1/searches/:id
  - Update name or filters
  - Return: Updated search

- [ ] DELETE /api/v1/searches/:id
  - Remove saved search
  - Return: 204 No Content

- [ ] POST /api/v1/searches/:id/execute
  - Apply saved filters
  - Update lastUsedAt
  - Return: Search results (same as regular search)
```

**Frontend Tasks:**

```typescript
- [ ] "Save this search" button on search page:
  - Location: Above search results
  - Only show if filters are applied
  - Click → Modal: "Name this search"
  - Input field + Save button
  - Success toast: "Search saved!"

- [ ] Saved searches dropdown:
  - Location: Search page header
  - Dropdown list of saved searches
  - Each item shows:
    - Name
    - Filter summary (badges)
    - "Edit" and "Delete" icons
  - Click item → Apply filters and execute search

- [ ] Create /searches page (optional):
  - Grid of saved searches as cards
  - Each card:
    - Name (editable on click)
    - Filter summary
    - "Run Search" button
    - "Edit Filters" button
    - "Delete" button
  - Empty state: "No saved searches yet"

- [ ] Dashboard integration:
  - "Saved Searches" quick access
  - Show 3 most recent
  - "View All" link
```

**Testing:**
- [ ] Save search with name
- [ ] Load and execute saved search
- [ ] Update saved search name
- [ ] Delete saved search
- [ ] Test 10 saved searches limit
- [ ] Test filter persistence

**Estimated Hours:** 12 hours

---

**Week 8 Total Estimated Hours:** 68 hours (was 30)

**Week 8 Deliverables:**
- ✅ Interest system (original)
- ✅ Dashboard with tabs (original)
- ✅ **NEW: Shortlist/Favorites**
- ✅ **NEW: Block/Ignore Users**
- ✅ **NEW: Saved Searches**
- **Preview link sent to you for testing**

---

## WEEK 9-10: PREMIUM PLANS & PAYMENTS (ENHANCED)

### **Week 9-10: Premium Features + Profile Boost**

#### **Original Features:** *(Same as v1.0)*
- Premium subscription plans
- PhonePe integration
- Payment webhooks

#### **NEW FEATURE 4: Profile Boost (Featured Listing)**

**User Story:** As a premium user, I want to boost my profile to appear at the top of search results for better visibility.

**Backend Tasks:**

```typescript
// Database Schema Update:
model Profile {
  // ... existing fields
  
  // NEW fields:
  isBoosted     Boolean   @default(false)
  boostedUntil  DateTime? // Expiry of boost
  boostCount    Int       @default(0) // Lifetime boost count
  
  @@index([isBoosted, boostedUntil])
}

model BoostPurchase {
  id              String   @id @default(cuid())
  userId          String
  user            User     @relation(fields: [userId], references: [id])
  profileId       String
  profile         Profile  @relation(fields: [profileId], references: [id])
  amount          Float    // ₹500
  duration        Int      // 7 days
  startsAt        DateTime
  endsAt          DateTime
  paymentId       String   // Link to payment table
  createdAt       DateTime @default(now())
  
  @@index([userId])
  @@index([endsAt])
}

// API Endpoints:
- [ ] POST /api/v1/payments/boost
  - Body: { duration: 7 } // 7 days boost
  - Price: ₹500 for 7 days
  - Auth: Premium users only
  - Validation: Profile exists, not already boosted
  - Create PhonePe payment order
  - Return: Payment URL

- [ ] Webhook handling (POST /webhooks/phonepe):
  - On SUCCESS:
    - Update profile: isBoosted = true, boostedUntil = now + 7 days
    - Create BoostPurchase record
  
- [ ] GET /api/v1/profiles/me/boost-status
  - Return: { isBoosted, boostedUntil, daysRemaining }

- [ ] Cron job (daily):
  - Check boostedUntil < now
  - Set isBoosted = false for expired boosts
  - Send notification: "Your boost has expired"

// Search Integration:
- [ ] Update search query:
  - ORDER BY isBoosted DESC, compatibilityScore DESC, createdAt DESC
  - Boosted profiles always appear first
```

**Frontend Tasks:**

```typescript
- [ ] "Boost Profile" section in /premium page:
  - Card: "Get More Visibility"
  - Features:
    - "Appear at the top of search results"
    - "3x more profile views"
    - "Higher response rate"
  - Pricing: ₹500 for 7 days
  - "Boost Now" button

- [ ] Boost indicator on profile cards:
  - Badge: "⚡ Boosted" (lightning icon)
  - Premium gold color
  - Only visible to other users (not on own profile)

- [ ] User's own profile page:
  - Boost status card:
    - If boosted: "Your profile is boosted for X more days"
    - If not: "Boost your profile for better visibility"
    - "Boost Again" / "Boost Now" button

- [ ] Dashboard stats:
  - Show profile views increase during boost period
  - Graph: Views before vs during boost

- [ ] Search results:
  - Boosted profiles appear at top
  - Visual distinction (subtle gold border)
```

**Testing:**
- [ ] Purchase boost (sandbox payment)
- [ ] Verify profile appears first in search
- [ ] Test boost expiry (manual DB update for quick test)
- [ ] Test cron job for auto-expiry
- [ ] Test "already boosted" validation

**Estimated Hours:** 18 hours

---

#### **NEW FEATURE 5: Priority Support Badge**

**User Story:** As a premium user, I want to display a premium badge on my profile to show I'm a verified, serious user.

**Backend Tasks:**

```typescript
// No database changes needed - uses existing user.role

// API Enhancement:
- [ ] Include role in profile responses:
  - GET /api/v1/profiles/:id
  - Return: { ...profile, user: { role: 'PREMIUM' } }
```

**Frontend Tasks:**

```typescript
- [ ] Premium badge on profile cards:
  - Icon: Crown icon or "Premium" badge
  - Color: Gold/yellow
  - Location: Top-right corner of profile card
  - Tooltip: "Premium Member"

- [ ] Premium badge on full profile page:
  - Prominent placement near profile photo
  - "Premium Member since [date]" text

- [ ] Premium benefits modal:
  - Click badge → Show modal with premium benefits
  - "Upgrade to Premium" CTA for free users

- [ ] Search filters:
  - "Show only Premium members" toggle
  - Premium profiles highlighted in results
```

**Testing:**
- [ ] Verify badge shows for premium users
- [ ] Verify badge hidden for free users
- [ ] Test filter by premium status

**Estimated Hours:** 8 hours

---

**Week 9-10 Total Estimated Hours:** 86 hours (was 60)

**Week 9-10 Deliverables:**
- ✅ Premium plans (original)
- ✅ PhonePe integration (original)
- ✅ **NEW: Profile Boost (₹500/7 days)**
- ✅ **NEW: Priority Support Badge**
- **Preview link sent to you for testing**

---

## WEEK 11: REAL-TIME CHAT (ENHANCED)

### **Week 11: Chat + Photo Sharing + File Attachments**

#### **Original Features:** *(Same as v1.0)*
- Real-time text messaging
- Typing indicators
- Read receipts
- Daily contact limits

#### **NEW FEATURE 6: Photo Sharing in Chat**

**User Story:** As a user, I want to share additional photos in chat conversations.

**Backend Tasks:**

```typescript
// Database Schema Update:
model Message {
  id          String   @id @default(cuid())
  senderId    String
  receiverId  String
  
  content     String?  @db.Text // Made optional
  
  // NEW fields:
  messageType String   @default("TEXT") // TEXT, IMAGE, FILE
  imageUrl    String?  // Cloudinary URL
  fileName    String?  // For file attachments
  fileUrl     String?  // Cloudinary URL for files
  fileSize    Int?     // In bytes
  
  isRead      Boolean  @default(false)
  createdAt   DateTime @default(now())
}

// API Endpoints:
- [ ] POST /api/v1/messages/upload-image
  - Accept: multipart/form-data
  - Body: receiverId, image file
  - Validation:
    - File type: JPEG, PNG, WebP only
    - Max size: 5MB
    - Premium check OR mutual interest
  - Upload to Cloudinary (chat-images folder)
  - NO watermark for chat images
  - Resize: Max 1200x1200
  - Save message: messageType = IMAGE
  - Emit via WebSocket to receiver
  - Return: Message object

- [ ] POST /api/v1/messages/upload-file
  - Accept: multipart/form-data
  - Body: receiverId, file
  - Validation:
    - File type: PDF only (for horoscope)
    - Max size: 2MB
  - Upload to Cloudinary
  - Save message: messageType = FILE
  - Return: Message object

// WebSocket Enhancement:
- [ ] Update MessagesGateway:
  - Handle 'sendImage' event
  - Handle 'sendFile' event
  - Emit 'newMessage' with messageType
```

**Frontend Tasks:**

```typescript
- [ ] Chat window enhancements:
  - Attachment button (📎 icon) in input area
  - Click → Dropdown:
    - "Send Photo" 📷
    - "Send File" 📄
  
- [ ] Photo sharing:
  - File picker (accept image/*)
  - Image preview before sending
  - Crop tool (optional, nice-to-have)
  - Upload progress indicator
  - After upload: Image appears in chat bubble

- [ ] Image message bubble:
  - Thumbnail in chat (max 300px wide)
  - Click to open lightbox (full-screen view)
  - Download button in lightbox
  - Lazy loading for images

- [ ] File message bubble:
  - File icon with name
  - File size display
  - "Download" button
  - PDF preview in modal (optional)

- [ ] Chat loading:
  - Load images lazily as user scrolls
  - Skeleton loaders for images loading
```

**Testing:**
- [ ] Upload and send image
- [ ] Upload and send PDF
- [ ] Test file size limits
- [ ] Test file type restrictions
- [ ] Test image lightbox
- [ ] Test download functionality

**Estimated Hours:** 16 hours

---

#### **NEW FEATURE 7: File Attachments (PDFs)**

**User Story:** As a user, I want to share my horoscope PDF in chat.

**Backend Tasks:**

```typescript
// Covered in Photo Sharing backend above

- [ ] Additional validations:
  - Scan PDF for malware (optional, using ClamAV or similar)
  - Limit: 1 file per message
  - Rate limit: Max 10 files per day per user
```

**Frontend Tasks:**

```typescript
// Covered in Photo Sharing frontend above

- [ ] PDF viewer modal:
  - Use react-pdf library
  - Show PDF preview in modal
  - Page navigation for multi-page PDFs
  - Download button
```

**Testing:**
- [ ] Upload PDF horoscope
- [ ] View PDF in browser
- [ ] Download PDF
- [ ] Test malformed PDF handling

**Estimated Hours:** 8 hours

---

**Week 11 Total Estimated Hours:** 79 hours (was 55)

**Week 11 Deliverables:**
- ✅ Real-time text chat (original)
- ✅ Typing indicators (original)
- ✅ Read receipts (original)
- ✅ Daily contact limits (original)
- ✅ **NEW: Photo sharing in chat**
- ✅ **NEW: PDF file attachments**
- **Preview link sent to you for testing**

---

## WEEK 12: ADMIN DASHBOARD (ENHANCED)

### **Week 12: Admin Dashboard + Profile Analytics**

#### **Original Features:** *(Same as v1.0)*
- Admin authentication
- User search and management
- Change user status

#### **NEW FEATURE 8: "Who Viewed My Profile"**

**User Story:** As a premium user, I want to see who viewed my profile so I can connect with interested users.

**Backend Tasks:**

```typescript
// Database Schema:
model ProfileView {
  id          String   @id @default(cuid())
  
  viewerId    String
  viewer      User     @relation("Viewer", fields: [viewerId], references: [id])
  
  viewedProfileId String
  viewedProfile   Profile @relation("ViewedProfile", fields: [viewedProfileId], references: [id])
  
  viewedAt    DateTime @default(now())
  
  // Analytics
  duration    Int?     // Seconds spent on profile (optional)
  source      String?  // SEARCH, RECOMMENDED, DIRECT_LINK
  
  @@unique([viewerId, viewedProfileId, viewedAt]) // Prevent duplicate log within same second
  @@index([viewedProfileId, viewedAt])
  @@index([viewerId])
}

// API Endpoints:
- [ ] POST /api/v1/profiles/:id/view (called on profile page load)
  - Body: { source: 'SEARCH' | 'RECOMMENDED' | etc. }
  - Create ProfileView record
  - Don't log own profile views
  - Don't log multiple views within 1 hour (prevent spam)
  - Return: 204 No Content

- [ ] GET /api/v1/profiles/me/viewers (Premium only)
  - Query: page, limit, days (last 7, 30, all)
  - Return: List of users who viewed profile
  - Include: viewer profile data (photo, basic info)
  - Order by: viewedAt DESC
  - Group: Show unique viewers (latest view)

- [ ] GET /api/v1/profiles/me/viewers/count
  - Return: Total view count, unique viewers
  - Premium only

- [ ] GET /api/v1/profiles/me/views/analytics
  - Return: Views over time (last 7 days, 30 days)
  - Format: [{ date: '2025-10-01', views: 15 }, ...]
  - Premium only
```

**Frontend Tasks:**

```typescript
- [ ] Profile view logging:
  - On profile page load (useEffect)
  - Call POST /api/v1/profiles/:id/view
  - Silent (no UI indication)

- [ ] Create /profile/viewers page (Premium only):
  - Header: "Who viewed your profile"
  - Stats cards:
    - Total views (all time)
    - Views this week
    - Unique visitors
  - List of recent viewers:
    - Profile card with photo
    - "Viewed 2 hours ago"
    - "Send Interest" button
    - Click card → View their full profile
  - Filter by time: Last 7 days, 30 days, All time
  - Pagination

- [ ] Dashboard integration:
  - "Profile Views" card
  - Show total views
  - "See who viewed" link → /profile/viewers
  - Chart: Views over time (last 7 days)

- [ ] Free user experience:
  - Show blurred list: "3 people viewed your profile"
  - Blur profile photos
  - CTA: "Upgrade to Premium to see who viewed"
  - Click → Redirect to /premium

- [ ] Profile page (own):
  - Stats: "Your profile was viewed X times"
  - "See viewers" link (premium only)
```

**Testing:**
- [ ] View profile → Verify log created
- [ ] Premium user: See viewers list
- [ ] Free user: See blurred list + upgrade prompt
- [ ] Test duplicate prevention (1 hour window)
- [ ] Test analytics chart

**Estimated Hours:** 20 hours

---

**Week 12 Total Estimated Hours:** 70 hours (was 50)

**Week 12 Deliverables:**
- ✅ Admin dashboard (original)
- ✅ User management (original)
- ✅ **NEW: "Who Viewed My Profile" (Premium)**
- ✅ **NEW: Profile view analytics**
- **Preview link sent to you for testing**

---

## WEEK 13-14: PORTALS & STORIES *(No changes)*

**Week 13:** Portal Management (Religions & Communities)  
**Week 14:** Success Stories CMS & Reports

**Details:** Same as original v1.0

**Estimated Hours:** 95 hours total (no changes)

---

## WEEK 15-16: COMMUNITY PORTALS & WHATSAPP *(No changes)*

**Week 15:** Religion/Community sub-portals with SEO  
**Week 16:** WhatsApp integration, legal pages, final polish

**Details:** Same as original v1.0

**Estimated Hours:** 100 hours total (no changes)

---

## WEEK 17-18: FINAL TESTING & OPTIMIZATION (NEW)

### **Week 17: Comprehensive Testing**

**Focus:** Test all 53 features end-to-end

**Tasks:**

```typescript
Testing Sprint:
- [ ] Full regression testing (all features)
- [ ] Cross-browser testing (Chrome, Firefox, Safari, Edge)
- [ ] Mobile testing (iOS Safari, Android Chrome, responsive)
- [ ] Performance testing:
  - Lighthouse audit: Target 90+ all metrics
  - Load testing: 1000 concurrent users
  - Database query optimization
- [ ] Security audit:
  - OWASP ZAP scan
  - Penetration testing
  - SQL injection tests
  - XSS tests
- [ ] Accessibility audit (WCAG 2.1 Level A)
- [ ] UAT with you (full platform walkthrough)

Bug Fixes:
- [ ] Fix all critical bugs
- [ ] Fix all high-priority bugs
- [ ] Document known low-priority issues for Phase 2

Documentation:
- [ ] User guide (how to use the platform)
- [ ] Admin manual (how to manage)
- [ ] FAQ page expansion
- [ ] Help center content
```

**Estimated Hours:** 50 hours

---

### **Week 18: Polish & Pre-Launch**

**Focus:** Final polish and launch preparation

**Tasks:**

```typescript
UI/UX Polish:
- [ ] Final design review (consistency across all pages)
- [ ] Animation polish (smooth transitions)
- [ ] Loading states perfected
- [ ] Error messages improved
- [ ] Empty states designed
- [ ] Success states polished

Content:
- [ ] Homepage copy finalized
- [ ] All email templates tested
- [ ] SMS templates verified
- [ ] Legal pages reviewed (Terms, Privacy)

Performance:
- [ ] Image optimization audit
- [ ] Bundle size optimization
- [ ] Lazy loading verification
- [ ] Cache strategy verified
- [ ] CDN configuration optimized

Launch Prep:
- [ ] Production environment configured
- [ ] Monitoring alerts set up
- [ ] Backup strategy tested
- [ ] Rollback plan documented
- [ ] Launch checklist created
- [ ] Support processes defined
```

**Estimated Hours:** 45 hours

---

## WEEK 19: LAUNCH WEEK 🚀

### **Week 19: Final Verification & GO LIVE**

**Monday-Wednesday: Final Checks**

```typescript
- [ ] Full smoke testing on production
- [ ] DNS verification
- [ ] SSL certificates verified
- [ ] Email deliverability test
- [ ] SMS delivery test
- [ ] Payment gateway test (live mode, small amount)
- [ ] Admin access verified
- [ ] Monitoring dashboards verified
- [ ] All integrations tested
```

**Thursday: Soft Launch**

```typescript
- [ ] Enable site for limited users
- [ ] Monitor closely
- [ ] Fix any critical issues
- [ ] Gather initial feedback
```

**Friday: FULL LAUNCH**

```typescript
- [ ] Public announcement
- [ ] Social media posts
- [ ] Press release (if applicable)
- [ ] Monitor closely throughout weekend
- [ ] Celebrate! 🎉
```

**Estimated Hours:** 40 hours

---

## 📊 UPDATED TIMELINE SUMMARY

### **Week-by-Week Hours Breakdown:**

| Week | Phase | Hours | Cumulative | Features Delivered |
|------|-------|-------|------------|-------------------|
| 1 | Setup | 40 | 40 | Infrastructure |
| 2 | Auth | 40 | 80 | Registration, verification |
| 3 | Auth | 35 | 115 | Login, password reset |
| 4 | Profile | 50 | 165 | Onboarding 1-2, family, lifestyle |
| 5 | Profile | 50 | 215 | Onboarding 3-4, photos |
| 6 | Search | 60 | 275 | Advanced search filters |
| 7 | Interests | 30 | 305 | Interest system |
| 8 | Features | 68 | 373 | Dashboard, favorites, block, saved searches |
| 9-10 | Premium | 86 | 459 | Premium, payment, boost |
| 11 | Chat | 79 | 538 | Chat, photo/file sharing |
| 12 | Admin | 70 | 608 | Admin, who viewed profile |
| 13 | Portals | 45 | 653 | Portal management |
| 14 | Stories | 50 | 703 | Success stories, reports |
| 15 | Portals | 45 | 748 | Community portals |
| 16 | Launch Prep | 55 | 803 | WhatsApp, polish |
| 17 | Testing | 50 | 853 | Full testing |
| 18 | Polish | 45 | 898 | Final polish |
| 19 | Launch | 40 | 938 | GO LIVE! |

**Total Hours:** 938 hours  
**Total Weeks:** 19 weeks  
**Average:** 49.4 hours/week  

---

## 📋 COMPLETE FEATURE LIST (53 FEATURES)

### **✅ Features Included in Updated MVP:**

**Authentication & User Management (5)**
1. Email/Phone Registration
2. Email Verification
3. Phone OTP Verification
4. Login & Logout (JWT)
5. Password Reset

**Profile & Onboarding (8)**
6. Multi-step Onboarding Wizard (4 steps)
7. Age Validation (Hard Block: 21M/18F)
8. Religion/Community Dropdowns
9. Photo Upload (5 photos max)
10. Cloudinary Watermarking
11. Profile Completeness Score
12. ✨ **Family Details Section** (NEW)
13. ✨ **Lifestyle Fields** (Diet, Smoking, Drinking) (NEW)

**Search & Discovery (9)**
14. Basic Search
15. Pagination
16. Profile Cards
17. ✨ **Advanced Search Filters** (15+ options) (NEW)
18. Recommended Matches (Compatibility)
19. Recently Joined
20. ✨ **Shortlist/Favorites** (NEW)
21. ✨ **Block/Ignore Users** (NEW)
22. ✨ **Saved Searches** (NEW)

**Interest System (3)**
23. Send Interest
24. Receive Interest
25. Accept/Decline Interest

**Premium & Monetization (6)**
26. Premium Plans (1M, 3M, 1Y)
27. Introductory Offer (7 days)
28. PhonePe Payment Integration
29. Payment Webhooks
30. ✨ **Profile Boost** (Featured Listing) (NEW)
31. ✨ **Premium Badge** (NEW)

**Communication (5)**
32. Real-time Chat (WebSocket)
33. Typing Indicators
34. Read Receipts
35. Daily Contact Limits
36. ✨ **Photo Sharing in Chat** (NEW)
37. ✨ **File Attachments** (PDF) (NEW)

**Admin Dashboard (7)**
38. Admin Authentication
39. User Search & Management
40. Change User Status
41. Portal Management (Religions)
42. Portal Management (Communities)
43. Success Stories CMS
44. User Reports & Moderation
45. ✨ **"Who Viewed My Profile"** (Premium) (NEW)

**Community Portals (4)**
46. Religion Portal Pages (/hindu)
47. Community Landing Pages (/hindu/bunt)
48. Automatic Profile Cross-listing
49. SEO Optimization

**Additional Features (4)**
50. WhatsApp Support Integration
51. Legal Pages (Terms, Privacy)
52. Contact Form
53. Success Stories Display

**Total:** **53 Features** (was 42)

---

## 💰 UPDATED COST PROJECTION

### **Monthly Costs (19-Week Timeline):**

| Period | Users | Monthly Cost |
|--------|-------|--------------|
| Week 1-3 | 0 | $10-15 |
| Week 4-8 | 0-50 (testing) | $15-30 |
| Week 9-14 | 50-100 | $30-55 |
| Week 15-19 | 100-200 | $55-109 |
| **Launch (Month 5)** | 200-500 | $109-159 |
| Month 6-12 | 500-5000 | $159-300 |

**Break-even:** ~Month 7-8 (with 2% premium conversion)

---

## 🎯 SUCCESS METRICS (UPDATED)

### **Launch Criteria (Week 19):**

```
Must Have:
├─ All 53 features working ✅
├─ 80%+ test coverage ✅
├─ Zero critical bugs ✅
├─ Lighthouse score 90+ ✅
├─ Load test passed (1000 users) ✅
├─ Security scan clean ✅
├─ UAT approved by you ✅
└─ Payment tested (live mode) ✅
```

### **Post-Launch Targets (Month 1):**

```
User Metrics:
├─ 200-1000 registered users
├─ 75%+ profile completion rate
├─ 40%+ daily active users
├─ 3-5% premium conversion
└─ 20+ success stories (within 6 months)

Technical Metrics:
├─ 99.9% uptime
├─ <3s average page load
├─ <1% error rate
└─ <100ms API response time (p95)
```

---

## 📅 NEXT STEPS

### **Your Immediate Actions:**

1. **Review this updated roadmap** (30 min)
2. **Approve the 19-week timeline** (vs 16 weeks)
3. **Confirm 53 features** (vs 42 features)
4. **Start Week 1 setup** (as per 00-SETUP-GUIDE.md)

### **What I'll Do (Week 1):**

```
Day 1-2: You create service accounts
Day 3: I create GitHub repo with updated plan
Day 4: I set up infrastructure
Day 5: I implement database schema (with new tables)
Day 6: I deploy skeleton apps
Day 7: You get admin access + I provide updated docs
```

---

## 🎉 SUMMARY

**Updated Plan Highlights:**

- ✅ **53 features** (82% parity with Shaadi.com)
- ✅ **19 weeks** to launch (4.75 months)
- ✅ **11 critical features** added based on research
- ✅ **Highly competitive** with market leader
- ✅ **Still cost-effective** ($10-159/mo scaling)
- ✅ **Clear path to profitability** (Month 7-8)

**We're building a WORLD-CLASS matrimony platform!** 💍✨

---

**Ready to approve and start Week 1?** 🚀

Let me know if you have any questions about the updated plan!
