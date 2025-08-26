# Mythos Community v0.4.7

🚀 **Project Summary**  
A modular hub for multi-game communities — with SSO integration, character management, rank-based access, and cross-platform linking. Built using Next.js, Tailwind CSS, Prisma, and NextAuth.

---

## 🌐 Core Features

### 🔐 Auth & Identity
- Secure email/username login via NextAuth
- JWT-based sessions with real-time status
- OAuth linking for Discord, Steam, YouTube (more coming)
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

### 🧰 EVE Access (scope-sets) — since v0.4.7
- **Set-centric grants:** Each toon stores a single `grantedScopeSetId` (default **`eveplayer`**).
- **Rank-aware requirements:** The **highest** `GameRank.level` you hold defines the **required** set(s).
- **Corp-only check:** At least one **corp toon** must grant a required (or higher-level) set.
- **Smart warning:** Characters page warns on:
  - `NO_TOONS` (you have requirements but no linked toons),
  - `NO_CORP_TOONS` (no linked toon in our corp),
  - `MISSING_SET` (corp toon(s) exist, but none grant the top-level set).
- **Over-granting:** Granting a **higher-level** set also satisfies requirements; UI shows a small FYI.

### 🪐 EVE Operations Hub (`/games/eve-online`)
- Public info + lore, killboard section (placeholder)
- Discord + Forum callouts
- Logged-in users see toon summary + corp content
- Leadership access panel (for directors, CEOs)

### 📝 EVE Corp Applications — since v0.4.7.2
- Draft → Review → Submit flow on the application detail page.
- **Section-based progress** (weighted) with readiness checks; includes a **Discord** requirement.
- **Discord verification subsection**: shows linked state, username, and avatar; prompts to link via **/profile** if missing.
- **Main Toon** selection persists; the toon’s name appears on the detail page and in the applications list.
- **Save Draft / Save Changes** preserves answers and section states.
- **Submit Application**.
- Locked UX: form save is blocked with a clear alert; submit button disabled on non-DRAFT apps.



### 🎛️ Admin Panel Overhaul (`/admin`)
- Fully tabbed system: Users, System, Games, Logs, DB
- User Management:**
- System Tab:**
- Games Management (v0.4.1):
- Database tools

### 📊 Log Viewer
- **Timeframe Filters**: 24h, 7d, 15d, 30d, current month (client-side filtering).
- **Log Cleanup API**: Deletes all log entries; usable by cron or button.
- Game related log tab (v0.4.4)


### 🌌 Landing Experience
- Animated, parallax-scrolling landing page
- Dot-nav to sections (About, Games, Join)
- Games list loaded dynamically from DB


##### ⚡ Real-time Presence (v0.4.5)
- **See who’s online**: Member cards now show a green dot when a user is online.
- **“Last seen”**: When someone is offline, you’ll see how long ago they were last active.
- **Live updates**: Status changes appear instantly—no page refresh needed.
- **Members-only**: Presence is visible only to logged-in members.
- Session duration & multi-socket awareness (v0.4.7)
- Admin panel "Active users tab" functionality
 - Multi-socket warnings



---

## 🛠️ Tech Stack
- **Frontend:** Next.js 15, React 19, Tailwind CSS, Framer Motion
- **Backend:** TypeScript (Node.js runtime) with Prisma (TypeScript) talking to PostgreSQL.
- **Auth:** NextAuth (JWT), with modular provider support
- **Infra:** `.env`-based config, modular API routes, REST endpoints

---

> Built for the Mythos gaming community.
