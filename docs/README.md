# Mythos Community v0.5.0

## 📖 About This Project

**Mythos Community** is a comprehensive gaming community platform designed to bring together players across multiple games under one unified hub. Built specifically for the Mythos gaming community, this platform provides seamless integration with popular games like EVE Online, offering character management, application systems, and real-time community features.

The platform serves as a central hub where community members can manage their gaming identities, apply to join corporation activities, and access game-specific tools and information. With a focus on EVE Online integration, it provides everything from character linking and economy tracking to corporation application management and leadership tools.

---

🚀 **Project Summary**  
A modular hub for multi-game communities — with SSO integration, character management, rank-based access, and cross-platform linking. Built using Next.js, Tailwind CSS, Prisma, and NextAuth.

---

## 🌐 Working Features

### 🔐 Authentication & Identity
- Secure email/username login via NextAuth
- JWT-based sessions with real-time status
- OAuth linking for Discord, Steam, YouTube
- Role-aware profile with linked account indicators

### 👤 Member Dashboard & Profile
- Personalized dashboard with game-based tiles
- Profile page with avatar, bio, and linked services
- Modular sections for scalability across games

### 🎮 EVE Online Integration
- EVE SSO character linking (multi-toon)
- View portrait, corp, alliance, scopes per character
- "Set as Main", "Edit Access", and "Unlink" functionality
- Character summary block with sync info
- Rank-based visibility for corp/private tools

### 💰 EVE User Economy (v0.4.7.4)
- **Wallet Tab**: Personal wallet transactions and balance tracking
- **Market Tab**: Active orders, completed orders, and trading stats
- **Contracts Tab**: Active contracts, completed contracts, and contract stats
- **Industry Tab**: Active jobs, job history, and industry statistics
- **Mining Tab**: Mining overview, ledger, and ore statistics
- **Assets Tab**: Asset management with value tracking and filtering
- Single/Combined modes for all tabs with individual filters

### 📝 EVE Corporation Applications (v0.4.7.2)
- Draft → Review → Submit application flow
- Section-based progress with readiness checks
- Discord verification requirement
- Main toon selection and persistence
- Save draft functionality with form state preservation

### 🎯 EVE Application Management (v0.5.0)
- **Leadership Audit System**: Complete application review interface
- **Section-by-Section Review**: Individual approval/rejection of application sections
- **Visual Status Indicators**: Color-coded status with auditor information
- **Application Workflow**: Submit → Under Review → Accept/Reject with audit trail
- **Resubmission Support**: Address rejected sections and resubmit
- **Auditor Notes**: Leadership can add review notes visible to applicants
- **Application History**: Complete view of decided applications
- **Reopen Functionality**: Reopen decided applications for re-evaluation
- **Real-time Updates**: Live status updates between applicant and auditor views

### 💼 EVE Corporation Wallet Management (v0.5.0)
- **Wallet Divisions**: Corporation wallet division management
- **Balance Tracking**: Historical balance snapshots with timestamps
- **Transaction History**: Detailed wallet transaction logging
- **Journal Entries**: Comprehensive wallet journal with ref types
- **Leadership-Only Access**: Protected by rank guards for corp leadership

### 🪐 EVE Operations Hub
- Public info and lore sections
- Discord and Forum integration
- Logged-in users see toon summary and corp content
- Leadership access panel for directors and CEOs

### 🎛️ Admin Panel
- **User Management**: User administration and role management
- **System Monitoring**: System health and performance metrics
- **Games Management**: Game configuration and settings
- **Log Viewer**: Application and game logs with timeframe filters
- **Database Tools**: Database management and maintenance

### ⚡ Real-time Features
- **Online Presence**: See who's online with green dot indicators
- **Last Seen**: Display when users were last active
- **Live Updates**: Status changes appear instantly without page refresh
- **Multi-socket Support**: Session duration and multi-socket awareness
- **Active Users**: Admin panel for monitoring active users

### 🌌 Landing Experience
- Animated, parallax-scrolling landing page
- Dot-navigation to sections (About, Games, Join)
- Games list loaded dynamically from database

---

## 🛠️ Tech Stack
- **Frontend:** Next.js 15, React 19, Tailwind CSS, Framer Motion
- **Backend:** TypeScript (Node.js runtime) with Prisma (TypeScript) talking to PostgreSQL
- **Auth:** NextAuth (JWT), with modular provider support
- **Infra:** `.env`-based config, modular API routes, REST endpoints

---

> Built for the Mythos gaming community.