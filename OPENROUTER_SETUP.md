# OpenRouter API Setup Instructions

## How to Add Your OpenRouter API Key

1. **Get your OpenRouter API key:**
   - Go to [OpenRouter.ai](https://openrouter.ai/)
   - Sign up or log in to your account
   - Navigate to the API Keys section
   - Create a new API key

2. **Add the API key to the project:**
   - Open `src/services/aiService.js`
   - Find line 8: `const OPENROUTER_API_KEY = 'YOUR_OPENROUTER_API_KEY_HERE';`
   - Replace `'YOUR_OPENROUTER_API_KEY_HERE'` with your actual OpenRouter API key

   Example:
   ```javascript
   const OPENROUTER_API_KEY = 'you api key';
   ```

## Available Models

The current setup uses `anthropic/claude-3.5-sonnet` but you can change it to other available models:

- `anthropic/claude-3.5-sonnet` (recommended for quality)
- `anthropic/claude-3-haiku` (faster, cheaper)
- `openai/gpt-4o`
- `openai/gpt-3.5-turbo`
- `meta-llama/llama-3.1-8b-instruct`

To change the model, edit line 110 in `src/services/aiService.js`:
```javascript
model: 'anthropic/claude-3.5-sonnet', // Change this to your preferred model
```

## Security Note

**Never commit your API key to version control!** 

For production, consider using environment variables:
1. Create a `.env` file in the project root
2. Add: `VITE_OPENROUTER_API_KEY=your_api_key_here`
3. Update the code to use: `import.meta.env.VITE_OPENROUTER_API_KEY`

## Features

✅ **Removed Google Gemini integration**
✅ **Added OpenRouter integration with Claude 3.5 Sonnet**
✅ **Removed all mock/fallback data - requires real AI analysis**
✅ **60% score threshold blocking still active**
✅ **Accurate resume-to-job matching analysis**
✅ **Improved AI prompts for better analysis quality**

⚠️ **IMPORTANT: The application now requires a valid OpenRouter API key to function. No mock data is provided.**

The AI will now:
- Actually analyze resume content against job requirements
- Provide accurate skill matching
- Give realistic scores based on actual resume-job fit
- Ensure consistency between matched/missing skills and recommendations
