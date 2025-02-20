# Deep.Assistant Organization

Welcome to the Deep.Assistant organization! We are dedicated to building AI-powered applications that enhance user experiences across various platforms. Our current projects include:

- **[api-gateway](https://github.com/deep-assistant/api-gateway)**: A central API gateway managing backend services for our applications and direct API users.
- **[telegram-bot](https://github.com/deep-assistant/telegram-bot)**: A Telegram bot (Deep.GPT) providing AI-powered assistance.
- **[GPTutor](https://github.com/deep-assistant/GPTutor)**: A VK mini-app for AI-driven tutoring.

## Architecture Overview

The following diagram illustrates how our applications interact with each other and the backend services. Users can also directly access the API gateway for OpenAI-compatible services. Click on the components to visit their GitHub repositories.

```mermaid
graph TB

subgraph UserLayer["User Layer"]
    user_vk["VK Users"]
    user_tele["Telegram Users"]
    direct_api_users["Direct API Users"]
end

subgraph ApplicationLayer["Application Layer"]
    app_gptutor["GPTutor (React, Typescript)"]
    app_telebot["telegram-bot (Python)"]
end

subgraph MiddlewareLayer["Middleware Layer"]
    middleware_apigw["api-gateway (Node.js, JavaScript)"]
end

subgraph backendLayer["Backend Layer"]
    backend_ai["AI Model Service"]
    backend_db["Database"]
end

user_vk <--> app_gptutor
user_tele <--> app_telebot
direct_api_users <--> middleware_apigw
app_gptutor <--> middleware_apigw
app_telebot <--> middleware_apigw
middleware_apigw <--> backend_ai
middleware_apigw <--> backend_db

click app_gptutor "https://github.com/deep-assistant/GPTutor"
click app_telebot "https://github.com/deep-assistant/telegram-bot"
click middleware_apigw "https://github.com/deep-assistant/api-gateway"
```

## Getting Started

### For End-Users
- **Telegram Bot (Deep.GPT)**: Start chatting with our AI-powered assistant at [https://t.me/DeepGPTBot](https://t.me/DeepGPTBot). Use `/help` for a list of commands or `/api` to get your API key.
- **GPTutor**: Access our AI tutoring mini-app through our VK community at [http://vk.com/gptutor](http://vk.com/gptutor). Launch the app directly from the community page.

### For Developers
- **API Gateway**: Obtain an API key from [https://t.me/DeepGPTBot](https://t.me/DeepGPTBot) using `/api`, then follow the quick start guide below to integrate with our OpenAI-compatible API at [https://api.deep-foundation.tech/v1/](https://api.deep-foundation.tech/v1/).
- **Contributing**: Clone any repository, set it up using the README instructions, and submit a pull request. See [Contributing Guidelines](#contributing) below.

## Applications

### api-gateway
- **Description**: A central API gateway managing requests from GPTutor, telegram-bot, and direct users to various API providers (e.g., GPT, LLM, Image, Music). It’s OpenAI-compatible and accessible at [https://api.deep-foundation.tech/v1/](https://api.deep-foundation.tech/v1/).
- **Technology**: Built with Node.js and Express.js for routing.
- **Setup**: See the [api-gateway README](https://github.com/deep-assistant/api-gateway/blob/main/README.md).
- **Quick Start**:
  ```js
  import OpenAI from 'openai';

  const openai = new OpenAI({
    apiKey: "YOUR_API_KEY", // Get from /api command at https://t.me/DeepGPTBot
    baseURL: "https://api.deep-foundation.tech/v1/"
  });

  async function main() {
    const chatCompletion = await openai.chat.completions.create({
      messages: [{ role: 'user', content: 'Say this is a test' }],
      model: 'gpt-4o-mini',
    });
    console.log(chatCompletion.choices[0].message.content); // "this is a test"
  }

  main();
  ```

- **API Documentation**: See the [API Gateway Docs](https://github.com/deep-assistant/api-gateway/blob/main/docs/API.md) for advanced usage (e.g., streaming, Whisper transcription).

### telegram-bot
- **Description**: Branded as **Deep.GPT**, this Telegram bot offers AI-driven assistance. Start chatting at [https://t.me/DeepGPTBot](https://t.me/DeepGPTBot).
- **Technology**: Developed in Python using the python-Telegram-Bot library.
- **Setup**: Follow the [telegram-bot README](https://github.com/deep-assistant/telegram-bot/blob/main/README.md).
- **User Guide**: 
  - Start: Send `/start` to begin.
  - Help: Use `/help` for commands.
  - API Key: Get yours with `/api`.
  - Chat: Simply type your questions or prompts!

### GPTutor
- **Description**: A VK mini-app branded as **GPTutor**, offering AI-powered tutoring, particularly for Russian-speaking users. Access it at [http://vk.com/gptutor](http://vk.com/gptutor).
- **Technology**: Built with React and Typescript, integrated with [vk-mini-apps-API](https://github.com/VKCOM/vk-mini-apps-api).
- **Setup**: See the [GPTutor README](https://github.com/deep-assistant/GPTutor/blob/main/README.md).
- **User Guide**:
  - Access: Visit [http://vk.com/gptutor](http://vk.com/gptutor) and click the app link.
  - Use: Follow in-app prompts to ask questions or start tutoring sessions.

## Contributing
We welcome contributions! Please read our [Contributing Guidelines](https://github.com/deep-assistant/.github/blob/main/CONTRIBUTING.md) to get involved. Steps:
1. Fork the repository.
2. Follow setup instructions in the README.
3. Submit a pull request with your changes.

## License
All projects are licensed under the [Unlicense](https://unlicense.org/), granting maximum freedom to use and modify the code. Verify the license file in each repository.