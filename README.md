# Virtual Stream

## Overview
A desktop streaming application that provides real-time chat overlay and streaming features. Built with React and Electron for cross-platform compatibility and WebSocket for real-time communication.
![image](https://github.com/user-attachments/assets/3da16dd4-60fd-49a1-82d4-6456b728db7c)


## Tech Stack
- **Frontend:** React
- **Desktop Framework:** Electron
- **Real-time Communication:** WebSocket
- **Language:** JavaScript

## Features
- Desktop Application Support (Windows, macOS)
- Real-time Chat Overlay
- Customizable UI Settings
- Low Latency Communication
- Stream Integration Support

## Installation

### Prerequisites
- Node.js (v16 or higher)
- npm or yarn

### Development Setup
1. Clone the repository
```bash
git clone https://github.com/yngkim/Virtual-Stream.git
```

2. Install dependencies
```bash
npm install
# or
yarn install
```

3. Start the development server
```bash
npm run dev
# or
yarn dev
```

## Building
To create a production build:
```bash
npm run build
# or
yarn build
```
# Whisper Streaming with WebSocket

This project extends the [Whisper Streaming](https://github.com/ufal/whisper_streaming) implementation by incorporating additional features, including real-time AI-generated viewer comments.

## How It Works

### 1️⃣ Start the Real-Time Speech Recognition Model (Whisper Streaming Server)
```bash
python3 whisper_online_server.py --backend mlx-whisper --language ko --vac --model small
```
This command launches the Whisper streaming server, which processes real-time audio input and converts it into text.

### 2️⃣ Run the Virtual Viewers WebSocket Server
```bash
python3 virtual_viewers.py
```
This script receives transcribed text from Whisper, sends it to OpenAI API, and generates simulated viewer comments. The responses are then sent to a WebSocket client (e.g., a React frontend).

### 3️⃣ Provide Real-Time Audio Input Using FFmpeg
```bash
ffmpeg -f avfoundation -i ":0" -ac 1 -ar 16000 -f wav - | nc localhost 43007
```
This command captures microphone input, converts it to a 16kHz mono WAV format, and streams it to Whisper via port `43007`.

## Summary

- **Whisper Streaming** processes live audio and transcribes it into text.
- **Virtual Viewers WebSocket Server** takes the transcribed text and generates AI-powered viewer comments.
- **FFmpeg** captures microphone input and streams it to Whisper for real-time processing.

This setup enables real-time speech recognition and simulated audience interaction through WebSocket, making it ideal for AI-powered live streaming experiences. 🎙️💬🚀





## Contributing
Contributions are welcome! Please feel free to submit a Pull Request.

## License
This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.
