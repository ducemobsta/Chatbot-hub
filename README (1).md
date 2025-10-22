# Multi-Model AI Chat Application

## Project Overview

A ChatHub.gg-style multi-model chat interface that allows users to compare responses from different AI models side-by-side in real-time. Built with Next.js 14, TypeScript, and Tailwind CSS.

## Features

- **Multi-Model Chat**: Compare responses from multiple AI models simultaneously
- **Side-by-Side Comparison**: View responses in separate panels for easy comparison
- **Message Actions**: Copy, edit, retry, and delete messages
- **Model Selection**: Choose from various Google Gemini models
- **Image Generator**: Generate images using AI (coming soon)
- **Web Summarizer**: Summarize web pages (coming soon)
- **Custom Instructions**: Set custom instructions for AI responses
- **Local Storage**: API keys stored securely in browser localStorage

## Tech Stack

- **Framework**: Next.js 14 (App Router)
- **Language**: TypeScript
- **Styling**: Tailwind CSS v4
- **UI Components**: shadcn/ui (Radix UI primitives)
- **AI Integration**: Direct API calls to Google Gemini API
- **State Management**: React hooks (useState, useEffect)

## Project Structure

```
├── app/
│   ├── api/
│   │   └── chat/
│   │       └── route.ts          # Chat API endpoint with retry logic
│   ├── layout.tsx                # Root layout
│   ├── page.tsx                  # Main page
│   └── globals.css               # Global styles
├── components/
│   ├── ui/                       # shadcn/ui components
│   ├── chat-panel.tsx            # Individual chat panel with message actions
│   ├── image-generator.tsx       # Image generation tool
│   ├── multi-model-chat.tsx      # Main chat orchestrator
│   ├── settings-dialog.tsx       # Settings modal with API keys
│   ├── sidebar.tsx               # Navigation sidebar
│   └── web-summarizer.tsx        # Web summarization tool
└── lib/
    └── utils.ts                  # Utility functions
```

## Available Models

Currently supported Google Gemini models:
- **Gemini 2.5 Flash**: Fast, efficient responses
- **Gemini 2.5 Pro**: Advanced reasoning and longer context
- **Gemini 2.0 Flash (Experimental)**: Latest experimental features

## Build Instructions

### Prerequisites

- Node.js 18+ installed
- npm or yarn package manager
- Google AI API key (get from https://aistudio.google.com/app/apikey)

### Installation

1. Clone or download the project
2. Install dependencies:
   ```bash
   npm install
   ```

3. Set up environment variables (optional):
   ```bash
   # Create .env.local file
   GOOGLE_GENERATIVE_AI_API_KEY=your_api_key_here
   ```

4. Run development server:
   ```bash
   npm run dev
   ```

5. Open http://localhost:3000 in your browser

### Build for Production

```bash
npm run build
npm start
```

## Deployment

### Vercel (Recommended)

1. Push your code to GitHub
2. Import project in Vercel dashboard
3. Add environment variables in Vercel project settings:
   - `GOOGLE_GENERATIVE_AI_API_KEY` (optional)
4. Deploy

### Other Platforms

The app can be deployed to any platform that supports Next.js:
- Netlify
- AWS Amplify
- Railway
- Render
- Self-hosted with Docker

## Configuration

### API Keys

API keys can be configured in two ways:

1. **Settings Dialog** (Recommended for users):
   - Click Settings icon in header
   - Enter API keys in the API Keys tab
   - Keys are stored in browser localStorage

2. **Environment Variables** (For deployment):
   - Set `GOOGLE_GENERATIVE_AI_API_KEY` in .env.local
   - Keys from environment take precedence

### Custom Instructions

Set custom instructions in Settings > General tab to modify how AI models respond to your queries.

### Theme & Language

- **Theme**: Light/Dark mode (coming soon)
- **Language**: Auto-detect or manual selection
- **Send Shortcut**: Enter or Ctrl+Enter to send messages

## API Endpoints

### POST /api/chat

Send messages to AI models and receive responses.

**Request Body:**
```json
{
  "messages": [
    { "role": "user", "content": "Hello" }
  ],
  "model": "gemini-2.5-flash",
  "apiKeys": {
    "google": "your_api_key"
  }
}
```

**Response:**
```json
{
  "content": "Hi there! How can I help you today?"
}
```

**Error Handling:**
- Automatic retry with exponential backoff for 503 errors
- Up to 2 retries with 1s and 2s delays
- Graceful error messages displayed in chat

## Features in Development

- [ ] OpenAI GPT models support
- [ ] Anthropic Claude models support
- [ ] Image generation with multiple providers
- [ ] Web page summarization
- [ ] AI translation tool
- [ ] Dark mode
- [ ] Export chat history
- [ ] Share conversations
- [ ] Custom model configurations

## Troubleshooting

### API Key Issues

- Ensure API key is valid and has sufficient quota
- Check that key is properly saved in Settings
- Verify network connection to Google AI API

### Model Overload (503 Errors)

- The app automatically retries failed requests
- Try a different model if one is consistently overloaded
- Wait a few minutes and try again

### Messages Not Displaying

- Check browser console for errors
- Verify API key is configured
- Ensure JavaScript is enabled

## License

MIT License - feel free to use and modify for your projects.

## Support

For issues or questions, please check:
- Browser console for error messages
- Network tab for API request/response details
- Settings to verify API key configuration

---

**Last Updated**: 2025-10-21T03:54:13.106Z
**Version**: 1.0.0
**Build Date**: 10/20/2025
