# 🚀 KUDLA MATRIMONY - INITIAL SETUP GUIDE

**Version:** 1.0  
**Date:** October 2, 2025  
**Estimated Setup Time:** 2-3 hours  

---

## 📋 TABLE OF CONTENTS

1. [Prerequisites](#prerequisites)
2. [Service Account Setup](#service-account-setup)
3. [Domain & DNS Configuration](#domain--dns-configuration)
4. [Repository Setup](#repository-setup)
5. [Environment Configuration](#environment-configuration)
6. [Initial Deployment](#initial-deployment)
7. [Verification Checklist](#verification-checklist)

---

## 1. PREREQUISITES

### Required Accounts (You Already Have These ✅)
- ✅ Cloudflare account (domain registered)
- ✅ PhonePe merchant account
- ✅ fast2sms account
- ✅ Cloudinary account
- ✅ Resend account

### Accounts I'll Create For You
- ⏳ GitHub account (if you don't have one)
- ⏳ Vercel account (connected to GitHub)
- ⏳ Railway account (connected to GitHub)
- ⏳ Neon account (PostgreSQL)
- ⏳ Upstash account (Redis)
- ⏳ Sentry account (error tracking)
- ⏳ Better Stack account (uptime monitoring)

### Required Software (For Local Development - Optional)
```bash
# You don't need these, but if you want to run locally later:
- Node.js 20 LTS
- pnpm 8+
- Git
- VS Code (or your preferred editor)
```

---

## 2. SERVICE ACCOUNT SETUP

### 2.1 Vercel Setup

**What:** Frontend hosting (Next.js)  
**Cost:** FREE (Hobby plan)  

**Steps:**
1. Go to https://vercel.com/signup
2. Sign up with GitHub
3. Authorize Vercel to access your GitHub account
4. Skip project creation (I'll do this via CLI)

**What I Need From You:**
- ✅ Verify email from Vercel
- ✅ That's it! I'll handle the rest

---

### 2.2 Railway Setup

**What:** Backend hosting (NestJS)  
**Cost:** $5/month credit (free initially)  

**Steps:**
1. Go to https://railway.app/
2. Sign up with GitHub
3. Verify email
4. Skip project creation

**What I Need From You:**
- ✅ Add payment method (won't be charged until free credit exhausted)
- ✅ Verify email

---

### 2.3 Neon Setup

**What:** PostgreSQL database  
**Cost:** FREE (3GB storage)  

**Steps:**
1. Go to https://neon.tech/
2. Sign up with GitHub or email
3. Create project: `kudla-matrimony-db`
4. Region: `US East (Ohio)` (lowest latency to Railway)
5. Copy connection string

**What I Need From You:**
- ✅ Share the connection string with me (I'll add to environment variables)

**Connection String Format:**
```
postgres://username:password@ep-xyz.us-east-2.aws.neon.tech/kudla_matrimony?sslmode=require
```

---

### 2.4 Upstash Setup

**What:** Redis (caching & job queues)  
**Cost:** FREE (10k commands/day)  

**Steps:**
1. Go to https://upstash.com/
2. Sign up with GitHub or email
3. Create Redis database:
   - Name: `kudla-matrimony-redis`
   - Region: `US East (Virginia)` (close to Railway)
   - Type: Regional
4. Copy connection URL

**What I Need From You:**
- ✅ Share Redis URL (format: `redis://...`)

---

### 2.5 Sentry Setup

**What:** Error tracking  
**Cost:** FREE (5k events/month)  

**Steps:**
1. Go to https://sentry.io/signup/
2. Sign up with GitHub
3. Create organization: `kudla-matrimony`
4. Create two projects:
   - `kudla-matrimony-web` (Next.js)
   - `kudla-matrimony-api` (NestJS)
5. Copy DSN for both

**What I Need From You:**
- ✅ Share both DSN URLs

---

### 2.6 Better Stack Setup

**What:** Uptime monitoring  
**Cost:** FREE  

**Steps:**
1. Go to https://betterstack.com/
2. Sign up with email
3. Create monitor (I'll configure this after deployment)

**What I Need From You:**
- ✅ Just create account, I'll handle configuration

---

## 3. DOMAIN & DNS CONFIGURATION

### 3.1 Cloudflare DNS Setup

**Domain:** kudlamatrimony.com  
**Current Status:** Registered on Cloudflare ✅  

**DNS Records to Add:**

```dns
# Root domain → Vercel
Type: A
Name: @
Content: 76.76.21.21
Proxy: ✅ Proxied (orange cloud)
TTL: Auto

# www subdomain → Vercel
Type: CNAME
Name: www
Content: cname.vercel-dns.com
Proxy: ✅ Proxied (orange cloud)
TTL: Auto

# API subdomain → Railway
Type: CNAME
Name: api
Content: [railway-app-url].up.railway.app
Proxy: ✅ Proxied (orange cloud)
TTL: Auto

# Email routing (for support@kudlamatrimony.com)
# This will be configured in Cloudflare Email Routing section
```

**Steps:**
1. Log in to Cloudflare
2. Select `kudlamatrimony.com`
3. Go to **DNS** tab
4. Click **Add record**
5. Add the three records above

**Note:** I'll provide the Railway URL after backend deployment.

---

### 3.2 Cloudflare Email Routing

**Setup Email Forwarding:**

**Destination:** matrimonykudla@gmail.com  

**Steps:**
1. In Cloudflare dashboard, go to **Email** → **Email Routing**
2. Click **Enable Email Routing**
3. Add destination address: `matrimonykudla@gmail.com`
4. Verify email (check Gmail for verification link)
5. Create routing rules:

```
support@kudlamatrimony.com → matrimonykudla@gmail.com
info@kudlamatrimony.com → matrimonykudla@gmail.com
admin@kudlamatrimony.com → matrimonykudla@gmail.com
```

**Result:** All emails sent to `@kudlamatrimony.com` will forward to your Gmail ✅

---

### 3.3 Cloudflare SSL/TLS Settings

**Ensure proper SSL:**

1. Go to **SSL/TLS** tab
2. Set to **Full (strict)**
3. Enable **Always Use HTTPS**
4. Enable **Automatic HTTPS Rewrites**
5. Minimum TLS Version: **1.2**

---

### 3.4 Cloudflare Page Rules (Optional - Can Set Later)

**For Performance:**

```
Rule 1: Cache Images
URL: kudlamatrimony.com/images/*
Settings:
  - Cache Level: Cache Everything
  - Edge Cache TTL: 1 month

Rule 2: Force HTTPS
URL: http://kudlamatrimony.com/*
Settings:
  - Always Use HTTPS: On
```

---

## 4. REPOSITORY SETUP

### 4.1 GitHub Repository Creation

**Repository Details:**
- **Name:** `kudla-matrimony`
- **Visibility:** Public (as per your requirement)
- **Owner:** Your GitHub account

**I'll Create:**
- Main branch (production)
- Develop branch (staging)
- Branch protection rules
- GitHub Actions workflows

**What I Need:**
- ✅ Your GitHub username
- ✅ Add me as collaborator (if you want me to push directly)

---

### 4.2 Repository Structure (I'll Create)

```
kudla-matrimony/
├── apps/
│   ├── web/          # Next.js frontend
│   └── api/          # NestJS backend
├── packages/
│   └── shared/       # Shared types
├── docs/             # All documentation
├── .github/
│   └── workflows/    # CI/CD pipelines
└── ... (full structure as per plan)
```

---

## 5. ENVIRONMENT CONFIGURATION

### 5.1 Environment Variables - Frontend (Vercel)

I'll configure these in Vercel dashboard:

```bash
# API Configuration
NEXT_PUBLIC_API_URL=https://api.kudlamatrimony.com
NEXT_PUBLIC_WS_URL=wss://api.kudlamatrimony.com

# Environment
NEXT_PUBLIC_ENV=production

# Sentry
NEXT_PUBLIC_SENTRY_DSN=https://xxx@sentry.io/xxx
```

---

### 5.2 Environment Variables - Backend (Railway)

I'll configure these in Railway dashboard:

```bash
# Database
DATABASE_URL=postgres://... (from Neon)

# Redis
REDIS_URL=redis://... (from Upstash)

# JWT
JWT_SECRET=<generated-random-64-char-string>
JWT_EXPIRY=7d

# Cloudinary
CLOUDINARY_CLOUD_NAME=<your-cloud-name>
CLOUDINARY_API_KEY=<your-api-key>
CLOUDINARY_API_SECRET=<your-api-secret>

# Resend
RESEND_API_KEY=<your-resend-api-key>

# fast2sms
FAST2SMS_API_KEY=<your-fast2sms-api-key>

# PhonePe
PHONEPE_MERCHANT_ID=<your-merchant-id>
PHONEPE_SALT_KEY=<your-salt-key>
PHONEPE_ENVIRONMENT=production

# Frontend URL (for CORS & redirects)
FRONTEND_URL=https://kudlamatrimony.com

# Sentry
SENTRY_DSN=https://xxx@sentry.io/xxx

# WhatsApp
WHATSAPP_NUMBER=+91XXXXXXXXXX (your support number)

# Environment
NODE_ENV=production
PORT=8080
```

---

### 5.3 API Keys I Need From You

**Please provide these API keys/credentials:**

**Cloudinary:**
```
Cloud Name: _____________
API Key: _____________
API Secret: _____________
```

**Resend:**
```
API Key: _____________
```

**fast2sms:**
```
API Key: _____________
```

**PhonePe:**
```
Merchant ID: _____________
Salt Key: _____________
Environment: [Production / UAT]
```

**WhatsApp Support:**
```
Support Phone Number: +91__________
```

**You can send these securely via:**
- Encrypted file
- Password-protected document
- Secure sharing service (e.g., 1Password, Bitwarden)

---

## 6. INITIAL DEPLOYMENT

### 6.1 Deployment Sequence

**Week 1 - Day 1-2: Infrastructure Setup**

1. ✅ Create GitHub repository
2. ✅ Initialize monorepo with Turborepo
3. ✅ Set up Next.js app skeleton
4. ✅ Set up NestJS app skeleton
5. ✅ Configure Prisma schema
6. ✅ Run initial database migration

**Week 1 - Day 3-4: Service Connections**

7. ✅ Connect Vercel to GitHub repo
8. ✅ Configure Vercel environment variables
9. ✅ Deploy Next.js to Vercel
10. ✅ Connect Railway to GitHub repo
11. ✅ Configure Railway environment variables
12. ✅ Deploy NestJS to Railway

**Week 1 - Day 5-7: Integration & Testing**

13. ✅ Update DNS records with Railway URL
14. ✅ Test API connectivity
15. ✅ Seed database with initial data:
    - Religions (Hindu, Christian, Muslim)
    - Communities (Bunt, Billava, Roman Catholic, etc.)
16. ✅ Create first admin user (matrimonykudla@gmail.com)
17. ✅ Test email delivery (Resend)
18. ✅ Test SMS delivery (fast2sms)
19. ✅ Configure Sentry error tracking
20. ✅ Set up Better Stack monitoring

---

### 6.2 Deployment URLs

**After deployment, you'll have:**

```
Production Frontend: https://kudlamatrimony.com
Production API: https://api.kudlamatrimony.com
API Documentation: https://api.kudlamatrimony.com/docs (Swagger)
Admin Panel: https://kudlamatrimony.com/admin

Staging Frontend: https://kudla-matrimony-dev.vercel.app
Staging API: https://kudla-matrimony-api-staging.up.railway.app
```

---

## 7. VERIFICATION CHECKLIST

### 7.1 Post-Deployment Verification

**I'll verify all of these and send you confirmation:**

- [ ] ✅ Frontend loads at https://kudlamatrimony.com
- [ ] ✅ SSL certificate is valid (green padlock)
- [ ] ✅ API is accessible at https://api.kudlamatrimony.com/health
- [ ] ✅ Database connection is working
- [ ] ✅ Redis connection is working
- [ ] ✅ Cloudinary image upload works
- [ ] ✅ Email sending works (test email sent)
- [ ] ✅ SMS sending works (test OTP sent)
- [ ] ✅ Sentry captures errors
- [ ] ✅ Better Stack monitors uptime
- [ ] ✅ Admin login works (matrimonykudla@gmail.com)
- [ ] ✅ Swagger docs accessible
- [ ] ✅ WhatsApp button appears on site

---

### 7.2 Access Credentials

**After setup, I'll provide you with:**

**Admin Panel Login:**
```
URL: https://kudlamatrimony.com/admin
Email: matrimonykudla@gmail.com
Password: [secure-generated-password]
```

**Service Dashboards:**
```
Vercel: https://vercel.com/[your-account]/kudla-matrimony-web
Railway: https://railway.app/project/[project-id]
Neon: https://console.neon.tech/app/projects/[project-id]
Sentry: https://sentry.io/organizations/kudla-matrimony/
```

---

## 8. WHAT YOU NEED TO DO

### Immediate Actions Required:

1. **Create Accounts:**
   - [ ] Vercel (sign up with GitHub)
   - [ ] Railway (sign up with GitHub)
   - [ ] Neon (sign up, create database)
   - [ ] Upstash (sign up, create Redis)
   - [ ] Sentry (sign up, create projects)
   - [ ] Better Stack (sign up)

2. **Provide API Keys:**
   - [ ] Cloudinary credentials
   - [ ] Resend API key
   - [ ] fast2sms API key
   - [ ] PhonePe merchant credentials
   - [ ] WhatsApp support number

3. **Cloudflare Configuration:**
   - [ ] Add DNS records (I'll provide exact values)
   - [ ] Set up email routing to matrimonykudla@gmail.com
   - [ ] Verify email forwarding

4. **GitHub:**
   - [ ] Provide your GitHub username
   - [ ] Create repository or add me as collaborator

---

## 9. TIMELINE

**Setup Phase: Week 1 (7 days)**

| Day | Tasks | Your Actions Required |
|-----|-------|----------------------|
| **Day 1** | Create service accounts | Sign up for Vercel, Railway, Neon, Upstash, Sentry |
| **Day 2** | Provide API keys | Send Cloudinary, Resend, fast2sms, PhonePe credentials |
| **Day 3** | I set up GitHub repo | Provide GitHub username |
| **Day 4** | I configure services | Add DNS records in Cloudflare |
| **Day 5** | I deploy skeleton apps | Verify email routing works |
| **Day 6** | I test integrations | Test login to admin panel |
| **Day 7** | Final verification | Confirm all systems working ✅ |

**After Week 1:** I start building features (Week 2-16)

---

## 10. SUPPORT & QUESTIONS

**During Setup:**
- I'll provide daily updates on progress
- I'll notify you when action is needed from your side
- I'll share preview links as soon as they're available

**If You Have Issues:**
- Email verification not received → Check spam folder
- Can't access a service → Send me screenshot, I'll help troubleshoot
- API key questions → I'll provide documentation on where to find them

---

## 11. SECURITY NOTES

**Protect These Credentials:**
- 🔒 Never commit API keys to Git
- 🔒 Use password manager for service credentials
- 🔒 Enable 2FA on all accounts (Cloudflare, Vercel, Railway, etc.)
- 🔒 Share API keys with me via secure method only

**I Will:**
- ✅ Store all secrets in environment variables (not in code)
- ✅ Use secret management in Vercel & Railway
- ✅ Never log sensitive data
- ✅ Encrypt all database connections

---

## 12. NEXT STEPS AFTER SETUP

**Once setup is complete (Day 7):**

1. ✅ You'll receive:
   - Admin login credentials
   - All service dashboard links
   - Test account credentials
   - Initial deployment URLs

2. ✅ I'll start building:
   - Week 2: User authentication
   - Week 3-4: Profile creation
   - Week 5-6: Search functionality
   - ... (see 05-PHASED-ROADMAP.md)

3. ✅ You'll receive:
   - Daily progress updates
   - Preview links for testing
   - Weekly summary reports

---

## 📞 READY TO START?

**To begin setup, please:**

1. Confirm you're ready to proceed
2. Start creating service accounts (Day 1-2)
3. Gather all API keys (Day 2)
4. I'll handle everything else!

**Estimated time investment from you:** 2-3 hours total across Week 1

**Let's build something amazing!** 🚀
