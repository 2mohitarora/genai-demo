# Slack Clone

## Project Description
A lightweight, anonymous team communication platform for casual conversations. No registration required - just pick a nickname and start chatting. Completely open access with persistent message history and browser-remembered nicknames.

## Target Audience
Small teams and casual groups (under 50 users) who want friction-free, anonymous communication

## Desired Features

### Core Messaging
- [ ] Real-time text messaging
- [ ] Channel-based conversations (completely open)
- [ ] Direct messages (1:1 and group)
- [ ] Message threading/replies
- [ ] Message editing and deletion (users can edit/delete their own messages)

### Simple Access & Identity
- [ ] Anonymous access with chosen nicknames
- [ ] Nickname persistence via browser storage
- [ ] No registration or authentication required
- [ ] Open workspace access (no barriers to entry)
- [ ] Anyone can create new channels

### Data Persistence
- [ ] Message history saved and persistent
- [ ] Channels exist permanently once created (no deletion/archiving)

### Notifications
- [ ] No push notifications

## Technical Stack
### Frontend
- [ ] Next.js (React framework)
- [ ] Tailwind CSS for styling
- [ ] shadcn/ui component library
- [ ] Mobile-responsive design
- [ ] Browser localStorage for nickname persistence

### Backend & Database
- [ ] Supabase (Backend-as-a-Service)
- [ ] PostgreSQL database (via Supabase)
- [ ] Drizzle ORM for database operations
- [ ] Supabase Realtime for live messaging functionality

### Infrastructure
- [ ] Supabase hosting for backend services

## Design Requests
- [ ] Clean, minimal interface optimized for casual conversation
- [ ] Mobile-responsive web design (no native mobile apps)
- [ ] Fast, lightweight user experience
- [ ] Intuitive nickname selection on first visit with browser storage
- [ ] shadcn/ui components for consistent, modern UI

## Other Notes
- Anonymous-first design philosophy
- Optimized for small-scale, casual team communication
- Session-based identity with browser storage for nickname persistence
- Permanent channel structure (channels never deleted)
- Leverage Supabase Realtime subscriptions for live updates