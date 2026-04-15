# Doula App Software Architecture Roadmap

## Project Goal
Build a mobile-first doula application using:

- Expo + TypeScript
- Supabase
- Claude Code
- VS Code
- GitHub

Core V1 features:

- Authentication
- User profile
- Community feed
- Comments and reactions
- Notifications
- Basic admin moderation

---

## Recommended Stack

### Frontend
- Expo (React Native)
- TypeScript
- React Hook Form
- Zod
- TanStack Query

### Backend and Infrastructure
- Supabase Auth
- Supabase Postgres
- Supabase Storage
- Supabase Realtime
- Supabase Row Level Security

### Developer Workflow
- GitHub
- Claude Code
- VS Code
- Feature branches
- Pull request workflow

### Later-stage tools
- Sentry for crash reporting
- PostHog for analytics
- Expo Notifications for push notifications

---

# Roadmap

## Phase 1: Foundation

### 1. Define V1 scope
Focus only on the first useful version of the app.

Included in V1:
- Login and signup
- User profile
- Community feed
- Comments
- Reactions
- Notifications
- Moderation basics

Excluded from V1:
- Video calls
- AI assistant
- Advanced search
- Payments
- Complex chat system

### 2. Set up repository structure
Suggested branch strategy:
- `main` for production
- `develop` for integration
- `feature/*` for scoped work

Suggested top-level structure:

```text
src/
  app/
  components/
  features/
    auth/
    profile/
    feed/
    comments/
    notifications/
    admin/
  lib/
  hooks/
  services/
  types/
  utils/
```

### 3. Create project rules for Claude Code
Create a `CLAUDE.md` file with rules such as:
- Use Expo + TypeScript
- Prefer functional components
- Use React Hook Form + Zod for forms
- Never store secrets in client code
- Every database change must include migration files
- Every screen must include loading, empty, and error states

### 4. Configure local development environment
Tasks:
- Create Expo app
- Configure TypeScript
- Add environment variables
- Install Supabase client
- Validate local startup

---

## Phase 2: Supabase Backend Architecture

### 5. Design the database schema
Core tables:

#### `profiles`
- `id`
- `role`
- `full_name`
- `username`
- `bio`
- `city`
- `photo_url`
- `created_at`

#### `posts`
- `id`
- `author_id`
- `content`
- `image_url`
- `created_at`

#### `comments`
- `id`
- `post_id`
- `author_id`
- `content`
- `created_at`

#### `reactions`
- `id`
- `post_id`
- `user_id`
- `type`

#### `notifications`
- `id`
- `user_id`
- `type`
- `title`
- `body`
- `is_read`
- `created_at`

#### `reports`
- `id`
- `reporter_id`
- `target_type`
- `target_id`
- `reason`
- `status`
- `created_at`

### 6. Create SQL migrations
All schema changes should be stored as migrations:
- table creation
- indexes
- constraints
- policies

### 7. Enable Row Level Security
Apply RLS to all user-owned data.

Examples:
- users can update only their own profile
- users can create posts as themselves
- users can edit and delete only their own posts
- admins can view moderation data

### 8. Configure Supabase Auth
Authentication flows:
- Sign up with email and password
- Login
- Logout
- Forgot password
- Persist session

---

## Phase 3: Frontend Core Flows

### 9. Build navigation and route structure
Main app areas:
- Auth
- Feed
- Post details
- Profile
- Notifications
- Admin

### 10. Build authentication screens
Screens:
- Login
- Signup
- Forgot password

### 11. Build onboarding and profile completion
User types:
- Doula
- Client

Suggested profile fields for doulas:
- Full name
- City
- Bio
- Certifications
- Years of experience
- Service type

Suggested profile fields for clients:
- Full name
- City
- Due date optional
- Interests or topics

### 12. Build profile and edit profile screens
Include:
- Read profile data
- Edit profile data
- Avatar upload
- Proper loading and error states

---

## Phase 4: Community Architecture

### 13. Build community feed
Core capabilities:
- List posts
- Refresh feed
- Empty state
- Loading state

### 14. Build create post flow
Support:
- Text posts
- Text plus image posts

### 15. Build post details screen
Include:
- Full post content
- Comments section
- Reactions section

### 16. Build comments system
Capabilities:
- Add comment
- List comments
- Delete own comment if desired in V1 or V2

### 17. Build reactions system
Capabilities:
- React to post
- Remove reaction
- Count reactions

### 18. Build content ownership rules
Users should be able to:
- Delete their own posts
- Not edit or delete other users’ posts

---

## Phase 5: Notifications and Moderation

### 19. Add push notifications
Implementation path:
- Install Expo Notifications
- Ask permission on device
- Store push token
- Link token to user

### 20. Add in-app notifications
Notification events can include:
- Someone commented on a post
- Someone reacted to a post
- Admin announcement

### 21. Build report system
Allow reporting of:
- Posts
- Comments
- Possibly users in a future phase

### 22. Build admin moderation queue
Admin capabilities:
- Review reports
- Change report status
- Remove offending content if needed

### 23. Add admin authorization rules
Use role-based access to protect admin-only areas.

---

## Phase 6: QA, Observability, and Release

### 24. Test authentication flows
Checklist:
- Signup
- Login
- Logout
- Invalid password handling
- Password recovery
- Session expiration

### 25. Test data security
Checklist:
- User cannot edit another user profile
- User cannot delete another user post
- Admin can access moderation area

### 26. Test community interactions
Checklist:
- Create post
- Load feed
- Comment on post
- React to post
- Delete own post

### 27. Add monitoring and analytics
Recommended later additions:
- Sentry
- PostHog

### 28. Prepare release pipeline
Suggested release stages:
- Local development
- Internal testing
- QA on real devices
- Beta release
- Production release

---

# Suggested GitHub Project Structure

## Views
- Backlog
- In Progress
- Review
- Done
- Roadmap

## Custom fields
- Phase
- Priority
- Status
- Area
- Estimate

## Suggested issue groups
- Foundation
- Backend
- Frontend
- Community
- Notifications
- Moderation
- Release

---

# Suggested First 5 Tasks for Claude Code

1. Create the Expo TypeScript app structure for the doula app
2. Add Supabase client setup with environment variables
3. Generate SQL migrations for the core tables
4. Create authentication screens and session handling
5. Create profile completion and edit profile flow

---

# Suggested Future Enhancements

After V1 is stable, consider:
- Search by city or expertise
- Private groups
- Direct messages
- Premium subscriptions
- Teleconsultation scheduling
- Video call integration
- Educational content library

---

# Delivery Notes
This roadmap is optimized for:
- iterative development
- Claude Code task decomposition
- GitHub-based project management
- Supabase-first architecture
- mobile-first UX
