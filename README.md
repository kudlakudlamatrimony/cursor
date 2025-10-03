# 💍 Kudla Matrimony Portal

> **A modern, community-focused matrimony platform built with Next.js, NestJS, and cutting-edge web technologies.**

[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)
[![Next.js](https://img.shields.io/badge/Next.js-14-black)](https://nextjs.org/)
[![NestJS](https://img.shields.io/badge/NestJS-10-red)](https://nestjs.com/)
[![TypeScript](https://img.shields.io/badge/TypeScript-5-blue)](https://www.typescriptlang.org/)
[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg)](CONTRIBUTING.md)

---

## 🌟 Features

### Core Features (MVP - Phase 1)
- ✅ **User Authentication** - Secure email & phone verification
- ✅ **Profile Creation** - Multi-step onboarding wizard
- ✅ **Advanced Search** - Filter by age, religion, community, location, and more
- ✅ **Interest System** - Send and receive connection requests
- ✅ **Real-time Chat** - WebSocket-powered instant messaging
- ✅ **Premium Plans** - 3-tier subscription model with PhonePe integration
- ✅ **Admin Dashboard** - User management, content moderation, analytics
- ✅ **Community Portals** - SEO-optimized sub-portals (`/hindu/bunt`)
- ✅ **Success Stories** - CMS for managing couple testimonials
- ✅ **WhatsApp Support** - Floating support button

### Advanced Features (Phase 2-3)
- 🔄 Compatibility Scoring Algorithm
- 🔄 Horoscope Matching
- 🔄 Advanced Profile Fields (Astrology, Family Details)
- 🔄 Saved Searches & Email Digests
- 🔄 Profile Boost & Visibility Controls
- 🔄 Verified Badges

---

## 🏗️ Tech Stack

### Frontend
- **Framework:** Next.js 14 (App Router)
- **Language:** TypeScript
- **Styling:** Tailwind CSS + shadcn/ui
- **State Management:** TanStack Query + Zustand
- **Forms:** React Hook Form + Zod
- **Real-time:** Socket.IO Client

### Backend
- **Framework:** NestJS
- **Language:** TypeScript
- **Database:** PostgreSQL (Neon)
- **ORM:** Prisma
- **Cache:** Redis (Upstash)
- **WebSocket:** Socket.IO
- **Jobs:** BullMQ
- **Authentication:** JWT + Passport.js

### Infrastructure
- **Frontend Hosting:** Vercel
- **Backend Hosting:** Railway
- **CDN:** Cloudflare
- **Images:** Cloudinary
- **Email:** Resend
- **SMS:** fast2sms
- **Payments:** PhonePe
- **Monitoring:** Sentry + Better Stack

---

## 📁 Project Structure

```
kudla-matrimony/
├── apps/
│   ├── web/                 # Next.js frontend
│   └── api/                 # NestJS backend
├── packages/
│   └── shared/              # Shared types & utilities
├── docs/                    # Comprehensive documentation
│   ├── 00-SETUP-GUIDE.md
│   ├── 01-ARCHITECTURE.md
│   ├── 02-DATABASE-SCHEMA.md
│   ├── 03-API-DOCUMENTATION.md
│   ├── 04-IMPLEMENTATION-STRATEGY.md
│   ├── 05-PHASED-ROADMAP.md
│   ├── 06-TESTING-PLAN.md
│   ├── 07-DEPLOYMENT-STRATEGY.md
│   ├── 08-SECURITY-COMPLIANCE.md
│   ├── 09-PERFORMANCE-OPTIMIZATION.md
│   └── 10-MAINTENANCE-PLAN.md
├── scripts/
│   ├── setup.sh
│   ├── seed-database.ts
│   └── create-admin.ts
└── .github/
    └── workflows/           # CI/CD pipelines
```

---

## 🚀 Quick Start

### Prerequisites
- Node.js 20 LTS
- pnpm 8+
- PostgreSQL 15+ (or Neon account)
- Redis 7+ (or Upstash account)

### Installation

```bash
# Clone repository
git clone https://github.com/[your-username]/kudla-matrimony.git
cd kudla-matrimony

# Install dependencies
pnpm install

# Set up environment variables
cp apps/web/.env.example apps/web/.env.local
cp apps/api/.env.example apps/api/.env

# Edit .env files with your credentials
# See docs/00-SETUP-GUIDE.md for detailed instructions

# Run database migrations
cd apps/api
pnpm prisma migrate dev

# Seed initial data
pnpm prisma db seed

# Create admin user
pnpm run create-admin

# Start development servers
cd ../..
pnpm dev
```

**Frontend:** http://localhost:3000  
**Backend API:** http://localhost:8080  
**API Docs:** http://localhost:8080/docs  

---

## 📚 Documentation

### Getting Started
- [Setup Guide](docs/00-SETUP-GUIDE.md) - Initial setup instructions
- [Architecture Overview](docs/01-ARCHITECTURE.md) - System design & data flows
- [Database Schema](docs/02-DATABASE-SCHEMA.md) - Complete Prisma schema
- [API Documentation](docs/03-API-DOCUMENTATION.md) - REST & WebSocket APIs

### Development
- [Implementation Strategy](docs/04-IMPLEMENTATION-STRATEGY.md) - Coding standards & best practices
- [Phased Roadmap](docs/05-PHASED-ROADMAP.md) - Week-by-week development plan
- [Testing Plan](docs/06-TESTING-PLAN.md) - Testing strategies & coverage

### Operations
- [Deployment Strategy](docs/07-DEPLOYMENT-STRATEGY.md) - CI/CD & deployment
- [Security & Compliance](docs/08-SECURITY-COMPLIANCE.md) - Security measures
- [Performance Optimization](docs/09-PERFORMANCE-OPTIMIZATION.md) - Caching & optimization
- [Maintenance Plan](docs/10-MAINTENANCE-PLAN.md) - Monitoring & updates

---

## 🧪 Testing

```bash
# Run all tests
pnpm test

# Unit tests
pnpm test:unit

# Integration tests
pnpm test:integration

# E2E tests
pnpm test:e2e

# Test coverage
pnpm test:coverage
```

**Target Coverage:** 80%+

---

## 🚢 Deployment

### Production

```bash
# Deploy frontend (Vercel)
vercel --prod

# Deploy backend (Railway)
railway up
```

### Staging

```bash
# Deploy to staging
git push origin develop
# Auto-deploys to staging environments
```

**Environments:**
- **Production:** https://kudlamatrimony.com
- **Staging:** https://kudla-matrimony-dev.vercel.app
- **API Docs:** https://api.kudlamatrimony.com/docs

---

## 🔐 Environment Variables

### Frontend (.env.local)
```bash
NEXT_PUBLIC_API_URL=http://localhost:8080
NEXT_PUBLIC_WS_URL=ws://localhost:8080
NEXT_PUBLIC_ENV=development
```

### Backend (.env)
```bash
DATABASE_URL=postgresql://...
REDIS_URL=redis://...
JWT_SECRET=your-secret-key
CLOUDINARY_CLOUD_NAME=...
RESEND_API_KEY=...
FAST2SMS_API_KEY=...
PHONEPE_MERCHANT_ID=...
```

See [Setup Guide](docs/00-SETUP-GUIDE.md) for complete list.

---

## 📊 Project Status

### Current Phase: **Phase 0 - Setup** (Week 1)

**Progress:**
- [x] Documentation complete
- [ ] Infrastructure setup
- [ ] Initial deployment
- [ ] Admin panel access

**Next Phase:** Phase 1 - MVP Development (Weeks 2-16)

See [Phased Roadmap](docs/05-PHASED-ROADMAP.md) for detailed timeline.

---

## 🎯 Milestones

| Milestone | Target Date | Status |
|-----------|-------------|--------|
| Setup Complete | Week 1 | 🟡 In Progress |
| User Authentication | Week 2-3 | ⏳ Pending |
| Profile Creation | Week 4-5 | ⏳ Pending |
| Search & Matching | Week 6-8 | ⏳ Pending |
| Premium & Payments | Week 9-11 | ⏳ Pending |
| Chat System | Week 12-13 | ⏳ Pending |
| Admin Dashboard | Week 14-15 | ⏳ Pending |
| **MVP Launch** | **Week 16** | ⏳ Pending |

---

## 🤝 Contributing

We welcome contributions! Please see our [Contributing Guide](CONTRIBUTING.md) for details.

### Development Workflow
1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

### Code Style
- Follow TypeScript best practices
- Use ESLint & Prettier (configured)
- Write tests for new features
- Update documentation

---

## 📝 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

---

## 👥 Team

**Product Owner:** Kudla Matrimony  
**Email:** matrimonykudla@gmail.com  
**Support:** support@kudlamatrimony.com  

**Development:** AI-Powered Development Team

---

## 🙏 Acknowledgments

- [Next.js](https://nextjs.org/) - React framework
- [NestJS](https://nestjs.com/) - Backend framework
- [Prisma](https://www.prisma.io/) - Database ORM
- [shadcn/ui](https://ui.shadcn.com/) - UI components
- [Vercel](https://vercel.com/) - Frontend hosting
- [Railway](https://railway.app/) - Backend hosting
- [Cloudflare](https://www.cloudflare.com/) - CDN & security

---

## 📞 Support

**For setup issues:**
- See [Setup Guide](docs/00-SETUP-GUIDE.md)
- Check [API Documentation](docs/03-API-DOCUMENTATION.md)

**For feature requests:**
- Open an issue on GitHub
- Email: matrimonykudla@gmail.com

**For bugs:**
- Check existing issues
- Create new issue with reproduction steps
- Include error logs & screenshots

---

## 🗺️ Roadmap

### Phase 1: MVP (Weeks 1-16) ✅ Current
- Core features for launch
- Basic admin dashboard
- Premium subscriptions

### Phase 2: Enhancements (Weeks 17-24)
- Advanced matching algorithm
- Horoscope compatibility
- Saved searches
- Email digests

### Phase 3: Scale & Growth (Month 7+)
- Mobile apps (iOS & Android)
- Video call integration
- Advanced analytics
- Multi-language support

See [Phased Roadmap](docs/05-PHASED-ROADMAP.md) for detailed plan.

---

## ⭐ Star History

If you find this project useful, please consider giving it a star!

[![Star History Chart](https://api.star-history.com/svg?repos=[your-username]/kudla-matrimony&type=Date)](https://star-history.com/#[your-username]/kudla-matrimony&Date)

---

## 📈 Stats

![GitHub repo size](https://img.shields.io/github/repo-size/[your-username]/kudla-matrimony)
![GitHub commit activity](https://img.shields.io/github/commit-activity/m/[your-username]/kudla-matrimony)
![GitHub last commit](https://img.shields.io/github/last-commit/[your-username]/kudla-matrimony)

---

**Built with ❤️ for the Kudla community**

**Live Site:** [kudlamatrimony.com](https://kudlamatrimony.com) (coming soon)
