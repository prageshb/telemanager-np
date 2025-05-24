# Telegram Bot Manager

A powerful Telegram bot management system with multi-bot support, enhanced logging, and automatic member management.

## Features

- 🔐 Secure access control with admin management
- 🤖 Multi-bot support with resource management
- 📊 Automatic cleanup of expired members (every 30 minutes)
- 📝 Enhanced logging with local timestamps
- 🔄 Auto-recovery and error handling
- 📈 Resource monitoring and optimization
- 👥 Member management with invite links
- 📱 User-friendly commands and interface
- 🔍 Detailed system statistics and monitoring
- 🛡️ Support for hidden user accounts

## System Requirements

- Node.js 14.x or higher
- SQLite3
- Minimum 2GB RAM
- Multi-core CPU recommended
- Stable internet connection

## Installation

1. Clone the repository:
```bash
git clone <repository-url>
cd telegram-bot-manager
```

2. Install dependencies:
```bash
npm install
```

3. Create a `.env` file with the following variables:
```env
BOT_TOKEN=your_bot_token
SUPER_BOT_TOKEN=your_super_bot_token
```

4. Initialize the database:
```bash
npm run init-db
```

5. Start the bot:
```bash
npm start
```

## Database Structure

### Main Database (main.db)
- users: User information and registration
- admins: Administrator accounts
- groups: Managed Telegram groups
- plans: Membership plans
- member_access: Member access records
- managed_bots: Bot management records

### Bot-specific Databases (bot_[id].db)
- users: User information for specific bot
- admins: Admin records for specific bot
- groups: Groups managed by specific bot
- plans: Plans available in specific bot
- member_access: Member access records for specific bot

## Commands

### User Commands
- `/start` - Start the bot
- `/join` - View active memberships
- `/help` - Show help message

### Admin Commands
- `/addgroup` - Add a new group
- `/listgroups` - List all groups
- `/addplan` - Create a new plan
- `/listplans` - List all plans
- `/addmember` - Add a new member
- `/listmembers` - List all active members
- `/removemember` - Remove a member
- `/getuser` - Get user information
- `/dashboard` - View system statistics
- `/broadcast` - Send message to members
- `/cleanup` - Manually trigger cleanup
- `/teachme` - Show admin tutorial

### Super Admin Commands
- `/addbot` - Add a new bot to the system
- `/listbots` - List all managed bots
- `/removebot` - Remove a bot from the system
- `/botstats` - View bot statistics
- `/restartbot` - Restart a specific bot
- `/stopbot` - Stop a specific bot
- `/startbot` - Start a specific bot

## Resource Management

The system automatically manages resources based on available hardware:

### CPU-based Limits
- Maximum 5 bots per CPU core
- Example: 8-core system can handle up to 40 bots (CPU-wise)

### Memory-based Limits
- Maximum 80% of total system memory
- Per-bot memory limit: 10% of total system memory
- Example: 10GB RAM system can handle 8 bots (memory-wise)

### Batch Processing
- Bots are started in batches of 5
- System load is managed automatically
- Resource usage is continuously monitored

## Recent Updates

### Version 2.0.0
- Added multi-bot support
- Enhanced logging system with local timestamps
- Improved error handling and recovery
- Added resource monitoring and management
- Updated cleanup interval to 30 minutes
- Added support for hidden user accounts
- Enhanced message handling
- Added detailed system statistics
- Improved user registration process
- Added automatic member access management

### Version 1.1.0
- Added `/getuser` command
- Enhanced message handling
- Improved error handling
- Added user registration on first interaction
- Updated cleanup process

### Version 1.0.0
- Initial release
- Basic bot functionality
- Member management
- Group management
- Plan management
- Admin system

## Contributing

1. Fork the repository
2. Create your feature branch
3. Commit your changes
4. Push to the branch
5. Create a Pull Request

## License

This project is licensed under the MIT License - see the LICENSE file for details.

## Support

For support, please open an issue in the repository or contact the development team. 