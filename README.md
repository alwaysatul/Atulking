# Pixly — Instagram-style social app starter

A runnable full-stack social networking starter with its own name and branding. It is not affiliated with Instagram or Meta.

## Included
- Email/password signup and login (bcrypt password hashing, JWT sessions)
- Profiles, profile photos and bios
- Photo/video posts, feed, likes, comments and delete-own-post API
- Follow/unfollow and username search
- 24-hour story records and story viewer
- Reels-style video feed
- Direct messages over REST, with Socket.IO message events
- Chat attachments for any file type, privately downloadable by conversation participants (100 MB default limit)
- Notifications for follows, likes and comments
- Admin stats endpoint and admin user deletion endpoint
- SQLite database and local media uploads
- Responsive web interface

## Requirements
- Node.js 18+ and npm

## Run locally
1. Extract the ZIP and open a terminal in this folder.
2. Install packages: `npm install`
3. Copy `.env.example` to `.env`.
4. Set a long random `JWT_SECRET`, and change the admin email/password.
5. Start: `npm start`
6. Open http://localhost:3000

## Notes / production checklist
This is a starter/MVP, not a production-scale Instagram replacement. Before public launch:
- Use HTTPS and secure cookie-based sessions or carefully protect JWTs.
- Add email verification, password reset, rate limiting, CSRF protections where applicable, account recovery and abuse reporting.
- Add moderation, blocking, privacy controls, content takedown and age/safety policies.
- Move media and chat attachments to object storage/CDN; scan uploads and generate thumbnails. Configure MAX_ATTACHMENT_MB to change the chat file-size limit.
- Add pagination, database migrations, backups, logging and monitoring.
- Add message conversation list UX, read receipts, delivery state, realtime client updates and push notifications.
- Restrict admin routes further with role management and audit logs.
- Configure CORS, upload limits, file validation, and secrets for your deployment environment.

## Main API routes
- `POST /api/auth/register`, `POST /api/auth/login`
- `GET /api/me`, `PATCH /api/me`
- `GET /api/feed`, `POST /api/posts`, `DELETE /api/posts/:id`
- `POST /api/posts/:id/like`, `POST /api/posts/:id/comments`
- `GET /api/users/search`, `GET /api/users/:id`, `POST /api/users/:id/follow`
- `POST /api/stories`, `GET /api/stories`
- `GET /api/inbox`, `GET /api/messages/:userId`, `POST /api/messages/:userId`
- `GET /api/notifications`, `POST /api/notifications/read`
- `GET /api/admin/stats`, `DELETE /api/admin/users/:id`

All `/api` routes except register/login require `Authorization: Bearer <token>`.
