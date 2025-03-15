# Video Transcription Service

A dockerized service that transcribes YouTube videos, Instagram videos, and local video files using the Wit.ai API. Supports English and Arabic languages.

## Features

- Transcribes videos from:
  - YouTube (including Shorts)
  - Instagram (including Reels)
  - Local video files
- Supports English and Arabic languages
- Outputs transcripts as text files
- Fully containerized with Docker

## Prerequisites

- Docker and Docker Compose installed
- A Wit.ai API key
  - Create an account at [wit.ai](https://wit.ai)
  - Create a new app
  - Set up English and Arabic as supported languages
  - Get your API key from the Settings page

## Quick Start

1. Clone this repository:
   ```bash
   git clone https://github.com/yourusername/video-transcriber.git
   cd video-transcriber
   ```

2. Make the run script executable:
   ```bash
   chmod +x run.sh
   ```

3. Build the Docker image:
   ```bash
   docker-compose build
   ```

4. Run the transcription service:
   ```bash
   # For YouTube videos
   WIT_API_KEY=your_api_key ./run.sh --source "https://www.youtube.com/watch?v=VIDEOID" --type youtube --language english

   # For Instagram videos
   WIT_API_KEY=your_api_key ./run.sh --source "https://www.instagram.com/p/POSTID/" --type instagram --language arabic

   # For local videos (place them in the videos/ directory first)
   WIT_API_KEY=your_api_key ./run.sh --source "myvideo.mp4" --type local --language english
   ```

## Usage

### Command Line Arguments

- `--source`: URL of YouTube/Instagram video or path to local video file
- `--type`: Type of video source (`youtube`, `instagram`, or `local`)
- `--language`: Language for transcription (`english`, `arabic`, `en`, or `ar`)
- `--output`: (Optional) Output directory for transcripts (default: /app/transcripts)

### Examples

```bash
# Transcribe a YouTube video in English
WIT_API_KEY=your_api_key ./run.sh --source "https://www.youtube.com/watch?v=dQw4w9WgXcQ" --type youtube --language english

# Transcribe an Instagram video in Arabic
WIT_API_KEY=your_api_key ./run.sh --source "https://www.instagram.com/p/ABC123/" --type instagram --language arabic

# Transcribe a local video file in English
# (First put your video file in the videos/ directory)
WIT_API_KEY=your_api_key ./run.sh --source "myvideo.mp4" --type local --language english
```

## Directory Structure

- `videos/`: Place local video files here for transcription
- `transcripts/`: Transcribed output will be saved here

## Limitations

- The Wit.ai API has file size limitations for audio processing
- Processing long videos may take time
- Instagram API may change, affecting the downloader functionality

## License

[MIT License](LICENSE)
