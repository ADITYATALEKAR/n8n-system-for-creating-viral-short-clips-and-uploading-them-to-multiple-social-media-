# N8N AI Video Clipper Workflow 🎬

**n8n workflow architecture for automatically converting long-form videos into viral short clips and uploading them to multiple social media platforms**

![License](https://img.shields.io/badge/license-MIT-blue.svg)
![Python](https://img.shields.io/badge/python-3.11+-blue.svg)
![FFmpeg](https://img.shields.io/badge/FFmpeg-required-green.svg)

## Overview

This repository contains an n8n workflow architecture designed to intelligently segment long videos into engaging short-form content optimized for social media platforms. The workflow uses n8n's automation capabilities combined with AI-powered analysis to transform your long-form content into platform-ready clips with captions, thumbnails, and metadata.

The architecture includes Python components that can be integrated into n8n workflows for video processing, caption generation, and multi-platform distribution.

## Key Features

### 🎯 Intelligent Video Processing
- **Smart Segmentation**: Automatically identifies interesting segments in long videos
- **Customizable Clip Duration**: 10-60 seconds with configurable overlap
- **Quality Control**: Adjustable video quality and resolution settings
- **Format Optimization**: Outputs optimized for each social platform

### 📱 Multi-Platform Support
- **YouTube Shorts**: Direct upload with metadata
- **TikTok**: Content Posting API integration
- **Instagram Reels**: Graph API support
- **LinkedIn Videos**: Professional network distribution

### 🤖 AI-Powered Features
- **Auto Captions**: OpenAI Whisper integration for accurate subtitles
- **Smart Thumbnails**: Automated thumbnail generation
- **Content Analysis**: Intelligent segment selection
- **Metadata Generation**: Auto-generated titles, descriptions, and tags

### 🔄 N8N Workflow Integration
- **Custom Python Nodes**: Ready-to-integrate Python components for n8n
- **Webhook Triggers**: Start processing via HTTP requests
- **Database Logging**: Track processing status and results
- **Error Handling**: Robust error management within n8n workflows
- **Scheduling**: Automated video processing on schedules

## Quick Start

### Prerequisites

```bash
# Install FFmpeg (required for video processing)
# macOS
brew install ffmpeg

# Ubuntu/Debian
sudo apt update && sudo apt install ffmpeg

# Windows
# Download from https://ffmpeg.org/download.html
```

### Installation

```bash
git clone https://github.com/yourusername/ai-video-clipper.git
cd ai-video-clipper
pip install -r requirements.txt
```

### Basic Usage

```python
from video_clipper import VideoClipperApp

# Initialize the app
app = VideoClipperApp()

# Process a video
result = app.process_video('your_video.mp4')

print(f"Generated {result['clips_generated']} clips")
```

### Command Line Usage

```bash
# First-time setup
python video_clipper.py --setup

# Process a single video
python video_clipper.py path/to/video.mp4

# Batch process multiple videos
python video_clipper.py path/to/video/folder --batch

# Check analytics
python video_clipper.py --analytics
```

## Configuration

### Interactive Setup Wizard

Run the setup wizard for guided configuration:

```bash
python video_clipper.py --setup
```

### Manual Configuration

Create a `config.json` file:

```json
{
  "video_settings": {
    "clip_duration": 15,
    "overlap_seconds": 2,
    "max_clips": 10,
    "output_resolution": "1080:1920",
    "video_quality": 18
  },
  "upload_settings": {
    "platforms": ["youtube", "tiktok", "instagram"],
    "auto_publish": true,
    "stagger_uploads": true,
    "stagger_minutes": 30
  },
  "api_keys": {
    "youtube_client_id": "your_youtube_client_id",
    "youtube_client_secret": "your_youtube_client_secret",
    "tiktok_client_key": "your_tiktok_client_key",
    "instagram_access_token": "your_instagram_token"
  }
}
```

## API Integration Setup

### YouTube API
1. Create a project in [Google Cloud Console](https://console.cloud.google.com/)
2. Enable YouTube Data API v3
3. Create OAuth 2.0 credentials
4. Add your Client ID and Secret to config

### TikTok API
1. Apply for [TikTok for Developers](https://developers.tiktok.com/)
2. Create an app and get your Client Key
3. Implement OAuth flow for user authorization

### Instagram API
1. Create a [Facebook Developer](https://developers.facebook.com/) account
2. Set up Instagram Basic Display or Instagram Graph API
3. Generate access tokens for your account

## Advanced Usage

### Jupyter Notebook Integration

```python
import sys
sys.path.append('path/to/ai-video-clipper')

from video_clipper import VideoClipperApp

app = VideoClipperApp()

# Process with custom settings
result = app.process_video(
    'input_video.mp4',
    output_dir='custom_clips'
)

# Batch processing
video_list = ['video1.mp4', 'video2.mp4', 'video3.mp4']
batch_results = app.batch_process_videos(video_list, max_workers=3)
```

### Custom Processing Pipeline

```python
from video_clipper import VideoProcessor, ConfigManager

config = ConfigManager()
processor = VideoProcessor(config)

# Generate clips only
clips = processor.generate_clips('video.mp4')

# Add captions
clips_with_captions = processor.add_captions(clips)

# Create thumbnails
final_clips = processor.create_thumbnails(clips_with_captions)
```

## Architecture

The application follows a modular architecture:

- **ConfigManager**: Handles configuration and settings
- **VideoProcessor**: Core video processing and AI features
- **SocialMediaUploader**: Multi-platform upload management
- **AnalyticsTracker**: Performance monitoring and insights
- **VideoClipperApp**: Main orchestration class

## Dependencies

### Required
- Python 3.11+
- FFmpeg/FFprobe
- OpenAI Whisper
- requests
- google-auth packages

### Optional
- Jupyter notebook support
- Threading for batch processing
- Advanced analytics features

## Limitations & Considerations

- **API Keys Required**: You must provide your own social media API credentials
- **Rate Limits**: Each platform has specific rate limits that are automatically managed
- **Content Policy**: Ensure your content complies with each platform's guidelines
- **Processing Time**: Video processing can be CPU/GPU intensive for large files

## Contributing

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Disclaimer

This tool is for educational and legitimate content creation purposes. Users are responsible for:
- Obtaining proper API credentials
- Complying with platform terms of service
- Respecting copyright and content policies
- Managing their own upload quotas and rate limits

## Support

- 📖 [Documentation](docs/)
- 🐛 [Issue Tracker](https://github.com/yourusername/ai-video-clipper/issues)
- 💬 [Discussions](https://github.com/yourusername/ai-video-clipper/discussions)

---

**Made with ❤️ for content creators and developers**
