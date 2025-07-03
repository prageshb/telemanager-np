# Telegram Membership Manager Bot

A Telegram bot platform for managing group memberships with time-based access control. Now supports **multi-bot management** with process isolation and resource monitoring.

## Features

- **Multi-Bot Management**
  - Add, remove, start, stop, and monitor multiple bots from a single super admin interface
  - Each bot runs in its own process and database for full isolation
  - Resource-aware: system checks CPU and RAM before starting new bots
- **Group Management**
  - Add/remove groups
  - Automatic group registration
  - Group access control
  - Join request handling
- **Plan Management**
  - Create and manage membership plans
  - Set custom durations
  - Add/remove groups from plans
  - Edit plan details (name, duration, groups)
  - Automatic handling of plan changes for existing members
- **Member Management**
  - Add members to plans
  - Automatic member removal on expiry
  - Membership extension handling
  - Member access tracking
  - Expiry notifications
  - Join request approval for active members
- **Admin Features**
  - Admin user management
  - Broadcast messages to members
  - System statistics dashboard
  - Member list export
  - Manual cleanup trigger
- **Resource Management**
  - Per-bot process and database
  - System resource monitoring (CPU, RAM)
  - Batch bot startup
  - Automatic cleanup and error recovery

---

## Command Reference

### 🧑 User Commands
- `/start` — Start the bot and register yourself
- `/join` — View your active memberships and join groups (shows plans, groups, expiry, and join buttons)
- `/help` — Show help message

### 👮 Admin Commands (per-bot)
- `/addgroup` — Add a new group to the system
- `/listgroups` — List all groups
- `/removegroup` — Remove a group from the system
- `/addplan` — Create a new membership plan
- `/listplans` — List all plans
- `/editplan` — Edit an existing plan (name, duration, groups)
- `/removeplan` — Remove a plan
- `/addmember` — Add a member to a plan (with invite link generation and extension logic)
- `/listmembers` — List all active members (with pagination)
- `/removemember` — Remove a member from all plans/groups
- `/getuser` — Get user information (ID lookup)
- `/dashboard` — View system statistics (overall, plans, groups, memberships)
- `/broadcast` — Send a message (text/media) to all users or active members
- `/cleanup` — Manually trigger expired member cleanup
- `/export` — Export member data to CSV
- `/teachme` — Show admin tutorial guide

### 🦸 Super Admin Commands (superbot only)
- `/addbot` — Add a new bot to the system (requires bot token)
- `/listbots` — List all managed bots
- `/removebot` — Remove a bot from the system
- `/startbot` — Start a specific bot
- `/stopbot` — Stop a specific bot
- `/restartbot` — Restart a specific bot
- `/botstatus` — View status of all bots
- `/botadmins` — Manage admins for each bot
- `/startall` — Start all bots
- `/stopall` — Stop all bots
- `/botdatabase` — Show database path for each bot

---

## Membership & Plan Features

- Create plans with custom durations
- Add multiple groups to a plan
- Edit plan details at any time
- Automatic handling of plan changes:
  - Duration increase: extends remaining time
  - Duration decrease: recalculates remaining time
  - Groups added: creates access for existing members
  - Groups removed: revokes access for existing members
- Time-based access control
- Automatic member removal on expiry
- Expiry notifications
- Join request approval for active members
- Membership extension handling
- Access tracking and management

## System Features

- **Automatic Cleanup**: Runs every 30 minutes, removes expired members, revokes invite links, sends expiry notifications, updates member status
- **Error Handling**: Graceful error recovery, detailed error logging, automatic reconnection, resource monitoring
- **Security**: Admin-only commands, secure invite link handling, join request verification, access control enforcement

## Multi-Bot Resource Management

- Each bot runs in its own process and database (full isolation)
- Maximum bots per CPU core (default: 5)
- Maximum 80% of total system memory used
- Per-bot memory limit (default: 10% of total system memory)
- Bots started in batches (default: 5 at a time)
- System load and resource usage are continuously monitored

## Setup

1. Create a new bot with [@BotFather](https://t.me/BotFather)
2. Get your bot token
3. Add the bot to your groups and grant permissions:
   - Add Members
   - Ban Users
   - Invite Users
   - Manage Chat
4. Start the bot with `/start`
5. Use `/teachme` for admin tutorial
6. For super admin, set up the superbot with `SUPER_BOT_TOKEN` and use `/addbot` to add/manage other bots

## Database Structure

- **Main Database (superbot):**
  - `managed_bots`: Bot management records
  - `bot_admins`: Super admin and per-bot admin records
  - `bot_activity_logs`: Activity logs for all bots
- **Bot-specific Databases:**
  - `users`, `admins`, `groups`, `plans`, `member_access` (per bot)

## System Requirements

- Node.js 14.x or higher
- SQLite3
- Minimum 2GB RAM
- Multi-core CPU recommended
- Stable internet connection

## Recent Updates

### Version 2.0.0
- Added multi-bot support (superbot manager)
- Enhanced logging system with local timestamps
- Improved error handling and recovery
- Added resource monitoring and management
- Updated cleanup interval to 30 minutes
- Added support for hidden user accounts
- Enhanced message handling
- Added detailed system statistics
- Improved user registration process
- Added automatic member access management

## Contributing

1. Fork the repository
2. Create your feature branch
3. Commit your changes
4. Push to the branch
5. Create a Pull Request

## License

This project is closed source project.

## Support

For support and further information, DM <a href="https://t.me/fiestyseer">@FiestySeer</a> in Telegram. 
