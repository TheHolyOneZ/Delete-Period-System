# Delete-Period-System
The **Delete Period System** is an advanced scheduled deletion management tool that allows server administrators to schedule the deletion of various Discord elements (messages, channels, roles, etc.) at specific times in the future.
> 💡 **Built for the Zygnal Ecosystem — to download and use this extension, you must be part of the Zygnal Ecosystem.**  
> This extension (cog) is part of the **Zygnal Ecosystem** and is only available through its supported platforms.  
> You can use it with:  
> - The **[Discord Bot Framework](https://github.com/TheHolyOneZ/discord-bot-framework)** — ideal for developers who want full control and flexibility *(includes an integrated extension marketplace)*, or  
> - The **[ZygnalBot](https://zygnalbot.de)** — a prebuilt, plug-and-play Discord bot *(also includes an integrated extension marketplace)*.  
>
> Browse and install extensions at [zygnalbot.com/extension](https://zygnalbot.com/extension).  
> For help or community discussions, join us on Discord: [discord.gg/sgZnXca5ts](https://discord.gg/sgZnXca5ts)
# 🗑️ Delete Period System Documentation

## 📋 Overview

The **Delete Period System** is an advanced scheduled deletion management tool that allows server administrators to schedule the deletion of various Discord elements (messages, channels, roles, etc.) at specific times in the future. This system provides precise control over server cleanup operations with comprehensive logging, permission management, and safety features.

---

## 🚀 Getting Started

### 📝 Available Commands

| Command | Aliases | Description |
|---------|---------|-------------|
| **Main Panel** | `!deleteperiod` | `!dp` | Open the interactive deletion control panel |
| **View Deletion** | `!deleteperiod view <id>` | `!dp view <id>` | View detailed information about a scheduled deletion |
| **Manage Permissions** | `!deleteperiod permissions` | `!dp permissions` | Configure who can use different deletion types (Admin only) |

### 🎛️ **Interactive Control Panel**
The main interface provides access to all deletion types through an intuitive button-based system:
- **Delete Messages** 💬 - Schedule message deletion operations
- **Delete Channels** 📁 - Schedule text channel removal
- **Delete Voice Channels** 🎵 - Schedule voice channel removal  
- **Delete Categories** 📂 - Schedule category deletion (with or without channels)
- **Delete Roles** 👥 - Schedule role removal
- **Delete Webhooks** 🔗 - Schedule webhook deletion
- **Settings** ⚙️ - Configure system settings (Admin only)

---

## 🎯 Core Features

### 💬 **Message Deletion Options**

#### 🔗 **Delete by Message URL**
- **Purpose**: Delete specific messages using their Discord URLs
- **Usage**: Paste message URLs (one per line) and set deletion time
- **Best For**: Removing specific problematic messages
- **Example**: `https://discord.com/channels/123/456/789`

#### 📁 **Delete by Channel**
- **Purpose**: Purge all messages from selected channels
- **Usage**: Select channels from dropdown and set deletion time
- **Best For**: Complete channel cleanup
- **Warning**: This deletes ALL messages in selected channels

#### 👤 **Delete by User**
- **Purpose**: Remove all messages from specific users
- **Usage**: Enter user IDs/mentions and choose scope (current channel or server-wide)
- **Best For**: Removing spam or cleaning up after banned users
- **Scope Options**:
  - **Current**: Only the channel where command was used
  - **Server**: All channels in the server

#### ⏰ **Delete by Time Range**
- **Purpose**: Delete messages within specific time periods
- **Usage**: Choose from preset ranges or set custom timeframe
- **Preset Options**:
  - Last Hour
  - Last 24 Hours  
  - Last 7 Days
  - Last 30 Days
  - Custom Range (specify days)

#### 🔍 **Delete by Pattern**
- **Purpose**: Delete messages containing specific text patterns
- **Usage**: Enter text pattern to search for and delete
- **Best For**: Removing messages with specific keywords or phrases
- **Note**: Case-insensitive pattern matching

### 🏗️ **Server Structure Deletion**

#### 📁 **Channel Deletion**
- **Text Channels**: Remove text channels completely
- **Multi-Selection**: Delete multiple channels at once
- **Safety**: Cannot delete channels the bot cannot access

#### 🎵 **Voice Channel Deletion**
- **Voice Channels**: Remove voice channels and stage channels
- **Member Handling**: Automatically disconnects users before deletion
- **Category Preservation**: Removes channels but leaves categories intact

#### 📂 **Category Deletion**
- **Two Options**:
  - **Category Only**: Moves channels out of category, then deletes category
  - **Category + Channels**: Deletes all channels in category, then deletes category
- **Flexible Control**: Choose whether to preserve or remove channels

#### 👥 **Role Deletion**
- **Role Management**: Remove roles from server
- **Member Impact**: Automatically removes role from all members
- **Hierarchy Respect**: Cannot delete roles higher than bot's role

#### 🔗 **Webhook Deletion**
- **Webhook Cleanup**: Remove webhooks from channels
- **Automatic Discovery**: Scans all channels for webhooks
- **Selective Deletion**: Choose specific webhooks to remove

---

## 🔐 Permission & Security System

### 👑 **Permission Levels**
Configure who can use each deletion type:

#### 🎭 **Role-Based Access**
```
!dp permissions setroles messages @Moderator @Admin
```
- Assign specific roles that can use each deletion type
- Multiple roles can be assigned per deletion type
- Administrators always have access

#### 🔑 **Permission-Based Access**
```
!dp permissions setperms channels manage_channels
```
- Require specific Discord permissions
- Default permissions for each type:
  - **Messages**: `manage_messages`
  - **Channels**: `manage_channels`
  - **Categories**: `manage_channels`
  - **Roles**: `manage_roles`
  - **Webhooks**: `manage_webhooks`
  - **Voice Channels**: `manage_channels`

#### 🔄 **Reset to Defaults**
```
!dp permissions reset messages
```
- Restore default permission requirements
- Useful for fixing misconfigured permissions

### 🛡️ **Safety Features**
- **Administrator Override**: Server administrators can always use all features
- **Hierarchy Respect**: Cannot delete items above bot's permission level
- **Confirmation Systems**: Critical operations require confirmation
- **Audit Logging**: All actions are logged with user attribution

---

## ⚙️ System Configuration

### 📊 **Settings Panel** (Administrator Only)

#### 🔄 **Toggle System**
- **Enable/Disable**: Turn the entire system on or off
- **Status Display**: Shows current system state
- **Emergency Control**: Quickly disable if needed

#### 📝 **Log Channel Configuration**
- **Set Log Channel**: Choose where deletion logs are sent
- **Rich Logging**: Detailed embeds with action information
- **Remove Logging**: Disable logging if desired

#### 📋 **View Scheduled Deletions**
- **Active Deletions**: See all pending scheduled deletions
- **Deletion Details**: View type, time, and user information
- **Quick Overview**: Up to 10 most recent scheduled deletions

#### ❌ **Cancel Scheduled Deletions**
- **Cancel by ID**: Remove specific scheduled deletions
- **User Restrictions**: Users can only cancel their own deletions (unless admin)
- **Immediate Effect**: Cancellation takes effect immediately

---

## 📊 Monitoring & Logging

### 📈 **Deletion Tracking**
Each scheduled deletion includes:
- **Unique ID**: 8-character identifier for easy reference
- **Creation Time**: When the deletion was scheduled
- **Scheduled Time**: When the deletion will execute
- **User Attribution**: Who scheduled the deletion
- **Target Details**: What will be deleted

### 📋 **Audit Logging**
Comprehensive logging includes:
- **Action Type**: What type of deletion occurred
- **Status**: Success or failure
- **User Information**: Who performed the action
- **Detailed Results**: Number of items deleted, errors encountered
- **Timestamps**: Precise timing of all operations

### 🔍 **Deletion Details**
View complete information about any scheduled deletion:
```
!dp view abc12345
```
Shows:
- **Type**: What kind of deletion
- **Scheduled By**: User who created it
- **Status**: Pending, completed, or failed
- **Target Information**: Specific details about what will be deleted
- **Timing**: Created time, scheduled time, time remaining

---

## ⏰ Scheduling System

### 🕐 **Time Management**
- **Minute-Based Scheduling**: Schedule deletions from 1 minute to any future time
- **Automatic Execution**: System checks every minute for due deletions
- **Timezone Handling**: All times displayed in user's local timezone
- **Flexible Input**: Simple minute-based input (5, 30, 60, etc.)

### 🔄 **Execution Process**
1. **Validation**: Check if targets still exist
2. **Permission Check**: Verify bot still has required permissions
3. **Execution**: Perform the deletion operation
4. **Logging**: Record results and notify via log channel
5. **Cleanup**: Remove completed deletion from schedule

### ⚡ **Real-Time Updates**
- **Live Countdown**: See exactly when deletions will occur
- **Status Updates**: Real-time status of all scheduled operations
- **Automatic Refresh**: Interface updates as deletions complete

---

## 💡 Use Cases & Examples

### 🧹 **Server Cleanup**
- **Inactive Channels**: Schedule removal of unused channels
- **Old Messages**: Clean up messages older than specific timeframes
- **Spam Cleanup**: Remove messages from banned users
- **Event Cleanup**: Delete temporary channels after events

### 📅 **Scheduled Maintenance**
- **Weekly Cleanup**: Regular message purging in busy channels
- **Role Management**: Remove temporary roles after events
- **Webhook Maintenance**: Clean up unused webhooks
- **Category Reorganization**: Restructure server layout

### 🚨 **Emergency Response**
- **Raid Cleanup**: Quickly schedule cleanup after server raids
- **Content Removal**: Remove inappropriate content with delay for review
- **User Cleanup**: Remove all traces of problematic users
- **Channel Lockdown**: Schedule channel deletion during incidents

---

## 🆘 Troubleshooting

### ❌ **Common Issues**

**"Permission denied"**
- Check if you have the required permissions for that deletion type
- Verify your role is configured in the permission system
- Ensure you're not trying to delete items above your permission level

**"Target not found"**
- The item to be deleted may have already been removed
- Check if the channel/role/user still exists
- Verify IDs and URLs are correct

**"Bot missing permissions"**
- Bot needs appropriate permissions for each deletion type
- Check bot's role position in server hierarchy
- Ensure bot has access to target channels

**"Deletion failed to execute"**
- Target may have been deleted by someone else
- Bot permissions may have changed since scheduling
- Check audit logs for specific error details

### 🔧 **Best Practices**

#### ⚠️ **Safety Guidelines**
- **Test First**: Use small-scale tests before major deletions
- **Backup Important Data**: Save important messages/settings before deletion
- **Review Carefully**: Double-check targets before scheduling
- **Monitor Logs**: Watch audit logs for any issues

#### 📋 **Organization Tips**
- **Use Descriptive Names**: Clear role and channel names help avoid mistakes
- **Regular Cleanup**: Schedule regular maintenance to prevent buildup
- **Permission Management**: Regularly review who has deletion permissions
- **Log Channel**: Always configure a log channel for tracking

---

## 🌟 Advanced Features

### 🎯 **Bulk Operations**
- **Multi-Channel**: Delete multiple channels simultaneously
- **Multi-Role**: Remove several roles at once
- **Pattern Matching**: Delete messages matching specific patterns
- **Time-Based**: Clean up content from specific time periods

### 🔄 **Automation Integration**
- **Scheduled Maintenance**: Regular automated cleanup
- **Event-Based**: Trigger deletions based on server events
- **Conditional Logic**: Complex deletion rules and conditions
- **Batch Processing**: Handle large deletion operations efficiently

### 📊 **Analytics & Reporting**
- **Deletion Statistics**: Track cleanup operations over time
- **Performance Metrics**: Monitor system efficiency
- **User Activity**: See who uses the system most
- **Impact Analysis**: Understand deletion patterns and effects

---

## ⚡ Quick Reference

### 🚀 **Common Workflows**

#### 📝 **Message Cleanup**
1. `!dp` → Delete Messages → Choose method
2. Configure targets and timing
3. `!dp view <id>` to monitor
4. Check logs for completion

#### 🏗️ **Channel Management**
1. `!dp` → Delete Channels/Categories
2. Select channels from dropdown
3. Set deletion time
4. Monitor via settings panel

#### 👥 **Role Cleanup**
1. `!dp` → Delete Roles
2. Choose roles (respecting hierarchy)
3. Schedule deletion
4. Verify in audit logs

---
