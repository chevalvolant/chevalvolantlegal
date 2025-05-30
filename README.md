# Personal TikTok Content Automation Tool

A personal automation application for streamlining content posting to TikTok. This tool helps automate the uploading and scheduling of videos and photos to my personal TikTok account.

## Overview

This application is designed for **personal use only** to automate the posting of my own content to TikTok. It integrates with TikTok's Content Posting API to enable seamless uploading of videos and photos with proper captions, hashtags, and privacy settings.

**Note:** This is a non-commercial, personal-use application. No content from other users is processed, and no commercial services are provided.

## Features

- ✅ **Video Upload Automation** - Automatically post videos from local storage or URL
- ✅ **Photo Upload Support** - Upload single photos or photo carousels
- ✅ **Content Scheduling** - Schedule posts for optimal timing
- ✅ **Caption & Hashtag Management** - Add captions and hashtags programmatically
- ✅ **Privacy Controls** - Set appropriate privacy levels for each post
- ✅ **Draft Mode** - Upload content as drafts for manual review before publishing
- ✅ **OAuth 2.0 Integration** - Secure authentication with TikTok API

## Workflow Description

### 1. Content Preparation
- User organizes videos/photos in designated local folders
- Content metadata (captions, hashtags, privacy settings) defined in configuration files
- Optional scheduling information specified for each piece of content

### 2. Authentication Flow
- Application redirects user to TikTok OAuth authorization page
- User grants necessary permissions (`video.upload` or `video.publish` scope)
- Application receives and securely stores access tokens for API calls

### 3. Content Processing Pipeline
```
Local Content → Validation → TikTok API Upload → Status Monitoring → Completion
```

**Detailed Steps:**
1. **Content Validation** - Verify file formats, sizes, and compliance with TikTok guidelines
2. **API Initialization** - Call TikTok's `/v2/post/publish/video/init/` or `/v2/post/publish/content/init/` endpoints
3. **File Transfer** - Upload content to TikTok's servers via provided upload URLs
4. **Status Monitoring** - Poll `/v2/post/publish/status/fetch/` endpoint for processing updates
5. **Completion Handling** - Log results and handle any errors or retries needed

### 4. Post Management
- **Direct Posting**: Content published immediately with specified settings
- **Draft Mode**: Content uploaded to TikTok inbox for manual review and publication
- **Scheduling**: Content queued for posting at specified future times

### 5. Monitoring & Logging
- Track upload status and success rates
- Log API responses for debugging
- Monitor rate limits (6 requests per minute per user token)
- Handle token refresh as needed (tokens expire every 24 hours)

## Technical Architecture

### Core Components
- **Authentication Manager** - Handles OAuth flow and token management
- **Content Processor** - Validates and prepares content for upload
- **API Client** - Manages all TikTok API interactions
- **Scheduler** - Handles timing and queuing of posts
- **Configuration Manager** - Manages user settings and content metadata

### API Integration
- **Content Posting API** - Primary integration for uploading videos and photos
- **Creator Info API** - Retrieves user profile information for UI rendering
- **Status API** - Monitors upload and processing status

### Security & Privacy
- All access tokens encrypted and stored securely
- Personal content never shared or transmitted to third parties
- Compliance with TikTok's Terms of Service and API guidelines
- Rate limiting implemented to respect API constraints

## File Structure
```
personal-tiktok-automation/
├── src/
│   ├── auth/           # OAuth implementation
│   ├── api/            # TikTok API client
│   ├── content/        # Content processing logic
│   ├── scheduler/      # Scheduling functionality
│   └── config/         # Configuration management
├── content/
│   ├── videos/         # Local video storage
│   ├── photos/         # Local photo storage
│   └── metadata/       # Content descriptions and settings
├── config/
│   ├── app.json        # Application configuration
│   └── schedule.json   # Posting schedule
└── logs/               # Application logs
```

## Usage Guidelines

### Supported Content Types
- **Videos**: MP4 with H.264 encoding, max 300 seconds duration
- **Photos**: JPG, JPEG, WEBP formats (PNG not supported by TikTok)
- **Descriptions**: Up to 2,200 characters with hashtags and mentions

### API Compliance
- Respects TikTok's rate limits (6 requests per minute per user)
- Implements proper error handling and retry logic
- Follows TikTok's UX guidelines for content posting
- Displays content previews before posting (when using direct post mode)
- Allows user control over all posting settings

### Privacy & Content Restrictions
- **Private Mode**: All content from unaudited apps posted in private mode initially
- **Personal Content Only**: Only processes content created by the authenticated user
- **No Watermarking**: Does not add promotional watermarks or branding to content
- **User Consent**: All uploads require explicit user authorization

## Installation & Setup

### Prerequisites
- Node.js 16+ or Python 3.8+
- TikTok Developer Account with approved Content Posting API access
- Valid TikTok user account for testing

### Configuration
1. Register application with TikTok for Developers
2. Obtain Client Key and Client Secret
3. Configure OAuth redirect URLs
4. Set up local environment variables
5. Install dependencies and run initial setup

### First Run
1. Complete OAuth authentication flow
2. Test with a single piece of content in draft mode
3. Verify posting workflow and permissions
4. Configure content folders and scheduling preferences

## Development Status

**Current Version**: 1.0.0 (Personal Use)  
**Status**: In Development  
**TikTok API Approval**: Pending Review  

### Recent Updates
- Implemented OAuth 2.0 authentication flow
- Added support for photo uploads (TikTok's newest feature)
- Created content validation and error handling
- Built scheduling system for automated posting

### Planned Features
- Enhanced scheduling with timezone support
- Content analytics and performance tracking
- Automatic hashtag suggestions
- Integration with other personal automation tools

## Compliance Statement

This application is developed for **personal use only** and complies with:
- TikTok Developer Terms of Service
- TikTok Content Posting API Guidelines
- OAuth 2.0 security standards
- Data privacy and security best practices

**Commercial Use**: This application is not intended for commercial use, resale, or service provision to third parties.

## License

MIT License - Personal Use Only

## Contact

For questions about this personal automation tool, please contact [your-email@example.com]

---

**Disclaimer**: This is a personal automation tool for individual use. It is not affiliated with, endorsed by, or officially connected to TikTok in any way beyond using their public API for personal content management.
