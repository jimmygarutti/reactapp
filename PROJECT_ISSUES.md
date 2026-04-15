# Doula App GitHub Project Issues

This document breaks the software architecture roadmap into GitHub-Projects-ready items.

Suggested custom fields for GitHub Projects:
- Phase
- Priority
- Status
- Area
- Estimate

Suggested default values:
- Status: Backlog
- Priority: High, Medium, Low
- Estimate: XS, S, M, L

---

## Issue 01
**Title:** Define V1 scope for doula app  
**Phase:** Foundation  
**Priority:** High  
**Area:** Product  
**Estimate:** S

**Description:**
Define the first production scope for the doula application.

**Acceptance Criteria:**
- Authentication is included in scope
- User profile is included in scope
- Community feed is included in scope
- Comments and reactions are included in scope
- Notifications are included in scope
- Moderation basics are included in scope
- Video calls, payments, and advanced AI features are explicitly out of scope for V1

---

## Issue 02
**Title:** Set up repository structure and branching strategy  
**Phase:** Foundation  
**Priority:** High  
**Area:** DevOps  
**Estimate:** S

**Description:**
Prepare the repository for collaborative development using a clear folder structure and branch model.

**Acceptance Criteria:**
- `main` branch is reserved for production-ready code
- `develop` branch is used for integration
- Feature branch naming convention is defined
- Base `src/` folder structure exists
- README includes setup instructions

---

## Issue 03
**Title:** Add CLAUDE.md project rules  
**Phase:** Foundation  
**Priority:** High  
**Area:** DX  
**Estimate:** XS

**Description:**
Create a `CLAUDE.md` file that documents coding rules and project constraints for Claude Code.

**Acceptance Criteria:**
- Stack is documented as Expo + TypeScript + Supabase
- Functional components are required
- Form handling pattern is documented
- Rule for avoiding secrets in client code is documented
- Rule for migrations on schema changes is documented
- Rule for loading, empty, and error states is documented

---

## Issue 04
**Title:** Configure local Expo development environment  
**Phase:** Foundation  
**Priority:** High  
**Area:** Frontend  
**Estimate:** S

**Description:**
Initialize the Expo application and configure the local development environment.

**Acceptance Criteria:**
- Expo app is created
- TypeScript is configured
- App runs locally
- Environment variable strategy is defined
- Supabase client dependency is installed

---

## Issue 05
**Title:** Design Supabase database schema  
**Phase:** Backend  
**Priority:** High  
**Area:** Backend  
**Estimate:** M

**Description:**
Design the initial relational schema for the app’s core data model.

**Acceptance Criteria:**
- `profiles` table is defined
- `posts` table is defined
- `comments` table is defined
- `reactions` table is defined
- `notifications` table is defined
- `reports` table is defined
- Primary and foreign keys are specified

---

## Issue 06
**Title:** Create SQL migrations for core schema  
**Phase:** Backend  
**Priority:** High  
**Area:** Backend  
**Estimate:** M

**Description:**
Create migration files for the initial database schema and core indexes.

**Acceptance Criteria:**
- All core tables are created through migrations
- Constraints are added through migrations
- Basic indexes are added for post ordering and comment lookup
- Migrations can be reapplied in a fresh environment

---

## Issue 07
**Title:** Enable Row Level Security for user-owned tables  
**Phase:** Backend  
**Priority:** High  
**Area:** Security  
**Estimate:** M

**Description:**
Protect all user-owned data using Supabase Row Level Security.

**Acceptance Criteria:**
- RLS is enabled on all user-owned tables
- Users can update only their own profile
- Users can create posts as themselves
- Users can delete only their own posts
- Admin access rules are defined for moderation flows

---

## Issue 08
**Title:** Set up Supabase Auth flows  
**Phase:** Backend  
**Priority:** High  
**Area:** Auth  
**Estimate:** M

**Description:**
Implement authentication capabilities using Supabase Auth.

**Acceptance Criteria:**
- Email/password sign up is supported
- Login is supported
- Logout is supported
- Forgot password flow is supported
- Session persistence is working

---

## Issue 09
**Title:** Configure Supabase storage buckets  
**Phase:** Backend  
**Priority:** Medium  
**Area:** Storage  
**Estimate:** S

**Description:**
Prepare storage buckets and rules for avatars and post media.

**Acceptance Criteria:**
- `avatars` bucket is created
- `post-images` bucket is created
- Access policies are defined
- Upload paths are documented

---

## Issue 10
**Title:** Create app navigation and route structure  
**Phase:** Frontend  
**Priority:** High  
**Area:** Frontend  
**Estimate:** M

**Description:**
Build the main navigation and route organization for app flows.

**Acceptance Criteria:**
- Auth flow routes exist
- Main app routes exist
- Feed route exists
- Profile route exists
- Notifications route exists
- Admin route is reserved or protected

---

## Issue 11
**Title:** Build login screen  
**Phase:** Frontend  
**Priority:** High  
**Area:** Auth  
**Estimate:** S

**Description:**
Create the login screen and connect it to Supabase Auth.

**Acceptance Criteria:**
- Email field exists
- Password field exists
- Validation is applied
- Login action works
- Error handling is visible to the user

---

## Issue 12
**Title:** Build signup screen  
**Phase:** Frontend  
**Priority:** High  
**Area:** Auth  
**Estimate:** S

**Description:**
Create the signup screen and connect it to Supabase Auth.

**Acceptance Criteria:**
- Email and password signup works
- Form validation works
- Success and error states are handled
- New users are redirected correctly after signup

---

## Issue 13
**Title:** Build forgot password flow  
**Phase:** Frontend  
**Priority:** Medium  
**Area:** Auth  
**Estimate:** S

**Description:**
Implement password recovery flow.

**Acceptance Criteria:**
- User can request password reset email
- Success message is shown
- Error state is shown when request fails

---

## Issue 14
**Title:** Build onboarding and profile completion flow  
**Phase:** Frontend  
**Priority:** High  
**Area:** Profile  
**Estimate:** M

**Description:**
Create the onboarding flow that collects the first set of profile data.

**Acceptance Criteria:**
- User role can be selected
- Required profile fields are collected
- Profile row is created or updated after signup
- Form validation is applied

---

## Issue 15
**Title:** Build profile screen  
**Phase:** Frontend  
**Priority:** High  
**Area:** Profile  
**Estimate:** S

**Description:**
Display user profile data in a dedicated screen.

**Acceptance Criteria:**
- Profile data is fetched from Supabase
- Avatar is displayed when available
- Profile fields render correctly
- Loading and error states are implemented

---

## Issue 16
**Title:** Build edit profile screen  
**Phase:** Frontend  
**Priority:** High  
**Area:** Profile  
**Estimate:** M

**Description:**
Allow users to edit their profile fields.

**Acceptance Criteria:**
- Existing profile data preloads in the form
- Updates persist successfully
- Validation errors are shown
- Success state is handled

---

## Issue 17
**Title:** Implement avatar upload flow  
**Phase:** Frontend  
**Priority:** Medium  
**Area:** Storage  
**Estimate:** S

**Description:**
Allow users to upload and update their profile picture.

**Acceptance Criteria:**
- User can select an image
- Image uploads to Supabase Storage
- Uploaded image URL is saved to profile
- Failures are handled gracefully

---

## Issue 18
**Title:** Build community feed screen  
**Phase:** Community  
**Priority:** High  
**Area:** Feed  
**Estimate:** M

**Description:**
Create the main community feed that lists posts.

**Acceptance Criteria:**
- Posts are loaded from database
- Feed is ordered correctly
- Loading state exists
- Empty state exists
- Pull-to-refresh or refresh behavior exists

---

## Issue 19
**Title:** Build create post flow  
**Phase:** Community  
**Priority:** High  
**Area:** Feed  
**Estimate:** M

**Description:**
Allow users to create text posts and optional image posts.

**Acceptance Criteria:**
- Text-only posts can be created
- Text + image posts can be created
- Validation is applied
- Successful post creation updates the feed

---

## Issue 20
**Title:** Build post details screen  
**Phase:** Community  
**Priority:** High  
**Area:** Feed  
**Estimate:** M

**Description:**
Create a dedicated post details screen to show a post and its interactions.

**Acceptance Criteria:**
- Full post content is shown
- Comments are visible
- Reactions are visible
- Navigation to and from feed works correctly

---

## Issue 21
**Title:** Implement comments system  
**Phase:** Community  
**Priority:** High  
**Area:** Comments  
**Estimate:** M

**Description:**
Implement creation and rendering of comments on posts.

**Acceptance Criteria:**
- User can add a comment
- Comments are listed for a post
- Comment author is shown
- Error states are handled

---

## Issue 22
**Title:** Implement reactions system  
**Phase:** Community  
**Priority:** Medium  
**Area:** Reactions  
**Estimate:** S

**Description:**
Allow users to react to posts.

**Acceptance Criteria:**
- User can add a reaction
- User can remove or toggle reaction
- Reaction totals are displayed
- Duplicate user reactions are prevented according to product rules

---

## Issue 23
**Title:** Enforce post ownership rules  
**Phase:** Community  
**Priority:** High  
**Area:** Security  
**Estimate:** S

**Description:**
Ensure only the post owner can delete their own post.

**Acceptance Criteria:**
- Post owner can delete own post
- Other users cannot delete post
- UI respects ownership permissions
- Backend policies enforce ownership rules

---

## Issue 24
**Title:** Add loading, empty, and error states across core screens  
**Phase:** Frontend  
**Priority:** Medium  
**Area:** UX  
**Estimate:** M

**Description:**
Polish the UX by implementing non-happy-path states across key flows.

**Acceptance Criteria:**
- Auth screens handle loading and errors
- Profile screens handle loading, empty, and errors
- Feed handles loading, empty, and errors
- Comments flow handles loading and errors

---

## Issue 25
**Title:** Configure push notification permissions and token storage  
**Phase:** Notifications  
**Priority:** Medium  
**Area:** Notifications  
**Estimate:** M

**Description:**
Set up push notification permissions and store device tokens.

**Acceptance Criteria:**
- App requests push notification permission
- Device token is retrieved
- Device token is stored in the backend
- Failure states are handled

---

## Issue 26
**Title:** Build in-app notifications screen  
**Phase:** Notifications  
**Priority:** Medium  
**Area:** Notifications  
**Estimate:** S

**Description:**
Create a screen that lists notifications relevant to the user.

**Acceptance Criteria:**
- Notifications are loaded from database
- Read/unread state is visible
- Empty state exists
- Basic notification types are supported

---

## Issue 27
**Title:** Trigger notifications for core social events  
**Phase:** Notifications  
**Priority:** Medium  
**Area:** Notifications  
**Estimate:** M

**Description:**
Trigger notifications when meaningful feed events happen.

**Acceptance Criteria:**
- Comment event triggers notification
- Reaction event triggers notification
- Notification payload is associated with correct user
- Notifications are persisted for in-app viewing

---

## Issue 28
**Title:** Add report post and report comment flow  
**Phase:** Moderation  
**Priority:** High  
**Area:** Moderation  
**Estimate:** M

**Description:**
Allow users to report inappropriate posts or comments.

**Acceptance Criteria:**
- Report action exists in post UI
- Report action exists in comment UI
- Reason is captured
- Report is stored in backend

---

## Issue 29
**Title:** Build admin moderation queue  
**Phase:** Moderation  
**Priority:** High  
**Area:** Admin  
**Estimate:** M

**Description:**
Create an admin-only area to review reports and take moderation actions.

**Acceptance Criteria:**
- Admin can list reports
- Admin can inspect report details
- Admin can update report status
- Admin-only access is enforced

---

## Issue 30
**Title:** Implement admin role-based authorization  
**Phase:** Moderation  
**Priority:** High  
**Area:** Security  
**Estimate:** S

**Description:**
Protect admin routes and data using role-based authorization.

**Acceptance Criteria:**
- Admin role exists in profile model or equivalent auth layer
- Non-admin users cannot access admin screens
- Non-admin users cannot read moderation records
- Admin users can access moderation records

---

## Issue 31
**Title:** Test authentication flows end to end  
**Phase:** QA  
**Priority:** High  
**Area:** QA  
**Estimate:** S

**Description:**
Validate the full authentication lifecycle.

**Acceptance Criteria:**
- Signup works
- Login works
- Logout works
- Forgot password works
- Invalid credentials are handled correctly

---

## Issue 32
**Title:** Test RLS and access control rules  
**Phase:** QA  
**Priority:** High  
**Area:** QA  
**Estimate:** M

**Description:**
Validate that all critical access rules are correctly enforced.

**Acceptance Criteria:**
- User cannot modify another user profile
- User cannot delete another user post
- Non-admin cannot access moderation data
- Admin can access moderation data

---

## Issue 33
**Title:** Test profile and media upload flows  
**Phase:** QA  
**Priority:** Medium  
**Area:** QA  
**Estimate:** S

**Description:**
Validate profile editing and image upload behavior.

**Acceptance Criteria:**
- Profile updates persist correctly
- Avatar upload works
- Error cases are handled
- Uploaded media displays correctly

---

## Issue 34
**Title:** Test community interactions  
**Phase:** QA  
**Priority:** High  
**Area:** QA  
**Estimate:** M

**Description:**
Validate the full community interaction loop.

**Acceptance Criteria:**
- User can create post
- User can view post in feed
- User can comment
- User can react
- User can delete own post

---

## Issue 35
**Title:** Add crash monitoring with Sentry  
**Phase:** Release  
**Priority:** Medium  
**Area:** Observability  
**Estimate:** S

**Description:**
Add runtime error and crash monitoring.

**Acceptance Criteria:**
- Sentry SDK is installed
- App environment is configured
- Test error is captured successfully
- Release environment is identified correctly

---

## Issue 36
**Title:** Add product analytics with PostHog  
**Phase:** Release  
**Priority:** Medium  
**Area:** Analytics  
**Estimate:** S

**Description:**
Track product usage and key activation events.

**Acceptance Criteria:**
- PostHog SDK is installed or alternative is chosen
- Signup completion event is tracked
- Profile completion event is tracked
- Post creation event is tracked

---

## Issue 37
**Title:** Prepare internal testing build  
**Phase:** Release  
**Priority:** High  
**Area:** Release  
**Estimate:** S

**Description:**
Prepare the first installable build for internal testing.

**Acceptance Criteria:**
- App can be built successfully
- Environment config is correct for test build
- Internal testers can install build
- Critical flows are smoke tested

---

## Issue 38
**Title:** Prepare production release checklist  
**Phase:** Release  
**Priority:** High  
**Area:** Release  
**Estimate:** S

**Description:**
Create a go-live checklist for the production launch.

**Acceptance Criteria:**
- Environment variables are verified
- Monitoring is enabled
- Analytics is enabled
- Security rules are reviewed
- Release checklist is documented

---

# Suggested Epic Grouping

## Epic: Foundation
- Issue 01
- Issue 02
- Issue 03
- Issue 04

## Epic: Backend
- Issue 05
- Issue 06
- Issue 07
- Issue 08
- Issue 09

## Epic: Frontend
- Issue 10
- Issue 11
- Issue 12
- Issue 13
- Issue 14
- Issue 15
- Issue 16
- Issue 17
- Issue 24

## Epic: Community
- Issue 18
- Issue 19
- Issue 20
- Issue 21
- Issue 22
- Issue 23

## Epic: Notifications
- Issue 25
- Issue 26
- Issue 27

## Epic: Moderation
- Issue 28
- Issue 29
- Issue 30

## Epic: QA and Release
- Issue 31
- Issue 32
- Issue 33
- Issue 34
- Issue 35
- Issue 36
- Issue 37
- Issue 38
