# Implementation Plan

## Database Initialization
- [ ] Step 1: Define Database Schema with Drizzle ORM
  - **Task**: Create schema definitions for channels, messages, users (anonymous nicknames), and threads.
  - **Files**:
    - `db/schema/index.ts`: Define Drizzle ORM schemas (`channels`, `messages`, `users`, `threads`).
  - **Step Dependencies**: None
  - **User Instructions**: Run `npm run db:push` after defining schemas.

- [ ] Step 2: Seed Initial Channels, Users, and Messages
  - **Task**: Create initial seed data using Drizzle ORM including default channels (`general`, `random`, `help`), anonymous users (`anon1`, `anon2`, etc.), and initial messages for each channel.
  - **Files**:
    - `db/seed.ts`: Script populating channels, users, and a few messages per channel using Drizzle ORM.
  - **Step Dependencies**: Step 1
  - **User Instructions**: Execute seed script with `npm run db:push`.

## Shared UI Components
- [ ] Step 3: Create Core UI Components
  - **Task**: Develop reusable UI components (MessageBubble, ChannelList, NicknamePrompt, MessageInput).
  - **Files**:
    - `components/MessageBubble.tsx`
    - `components/ChannelList.tsx`
    - `components/NicknamePrompt.tsx`
    - `components/MessageInput.tsx`
  - **Step Dependencies**: None
  - **User Instructions**: Verify rendering through direct use in pages.

## Messaging and Channels
- [ ] Step 4: Implement Real-time Channel-based Messaging
  - **Task**: Integrate Supabase Realtime subscriptions for live channel messages.
  - **Files**:
    - `app/api/channels/[channelId]/messages/route.ts`
    - `hooks/useMessages.ts`
  - **Step Dependencies**: Steps 1, 3
  - **User Instructions**: None.

## Nickname Persistence and Anonymous Identity
- [ ] Step 5: Nickname Persistence via Browser Storage
  - **Task**: Implement nickname persistence using localStorage.
  - **Files**:
    - `hooks/useNickname.ts`
    - `components/NicknamePrompt.tsx`
  - **Step Dependencies**: Step 3
  - **User Instructions**: None.

## Frontend Pages and Routing
- [ ] Step 6: Set Up Routing and Channel Page
  - **Task**: Develop frontend routing and UI for channel viewing and messaging.
  - **Files**:
    - `app/channels/[channelId]/page.tsx`
    - `app/channels/page.tsx`
  - **Step Dependencies**: Steps 3, 4
  - **User Instructions**: None.

## Direct Messaging (DMs)
- [ ] Step 7: Implement Direct Messaging
  - **Task**: Backend and UI setup for direct messaging (1:1 and group).
  - **Files**:
    - `db/schema/dms.ts`
    - `app/api/dms/route.ts`
    - `components/DMList.tsx`
  - **Step Dependencies**: Steps 1, 4
  - **User Instructions**: Apply migrations after schema updates.

## Message Management
- [ ] Step 8: Message Editing and Deletion
  - **Task**: Allow users to edit and delete their messages.
  - **Files**:
    - `app/api/messages/[messageId]/route.ts`
    - `components/MessageBubble.tsx`
  - **Step Dependencies**: Steps 1, 4
  - **User Instructions**: None.

## Final UI Polish and UX Enhancements
- [ ] Step 9: Refine UI and User Experience
  - **Task**: Ensure polished, responsive UX across the application.
  - **Files**:
    - `app/globals.css`
    - Adjustments across UI components as needed.
  - **Step Dependencies**: All prior frontend tasks
  - **User Instructions**: None.
