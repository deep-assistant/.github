# Deep.Assistant Organization

Welcome to the Deep.Assistant organization! We are dedicated to building AI-powered applications that enhance user experiences across various platforms. Our current projects include:

- **[api-gateway](https://github.com/deep-assistant/api-gateway)**: A central API gateway managing backend services for our applications.
- **[telegrambot](https://github.com/deep-assistant/telegrambot)**: A Telegram bot providing AI-powered assistance.
- **[GPTutor](https://github.com/deep-assistant/GPTutor)**: A VK mini-app for AI-driven tutoring.

## Architecture Overview

The following diagram illustrates how our applications interact with each other and the backend services. Additionally, users can directly access the API gateway for OpenAI-compatible services and more. Click on the components to visit their respective GitHub repositories.

```mermaid
graph TB

subgraph UserLayer["User Layer"]
    user_vk["VK Users"]
    user_tele["Telegram Users"]
    direct_api_users["Direct API Users"]
end

subgraph ApplicationLayer["Application Layer"]
    app_gptutor["GPTutor (React, Typescript)"]
    app_telebot["telegrambot (Python)"]
end

subgraph MiddlewareLayer["Middleware Layer"]
    middleware_apigw["api-gateway (Node.js, JavaScript)"]
end

subgraph backendLayer["backend Layer"]
    backend_ai["AI Model Service"]
    backend_db["Database"]
end

user_vk --> app_gptutor
user_tele --> app_telebot
direct_api_users --> middleware_apigw
app_gptutor --> middleware_apigw
app_telebot --> middleware_apigw
middleware_apigw --> backend_ai
middleware_apigw --> backend_db

click app_gptutor "https://github.com/deep-assistant/GPTutor"
click app_telebot "https://github.com/deep-assistant/telegrambot"
click middleware_apigw "https://github.com/deep-assistant/api-gateway"
```

## Applications

### api-gateway
- **Description**: Serves as the central API gateway, managing requests from GPTutor, telegrambot, and direct users to various API providers for GPT, LLM, Image, Music, and other services. It is OpenAI-compatible and accessible via `https://api.deep-foundation.tech/v1`.
- **Technology**: Implemented in Node.js with Express.js for routing.
- **Setup**: Detailed setup instructions can be found in the [api-gateway README](https://github.com/deep-assistant/api-gateway/blob/main/README.md).

### telegrambot
- **Description**: A Telegram bot, branded as **Deep.GPT**, that offers AI-driven assistance, processing user inputs and providing intelligent responses. [Start chatting here](https://t.me/DeepGPTBot).
- **Technology**: Developed in Python, utilizing the python-Telegram-Bot library for Telegram API interactions.
- **Setup**: Detailed setup instructions can be found in the [telegrambot README](https://github.com/deep-assistant/telegrambot/blob/main/README.md).

### GPTutor
- **Description**: A VK mini-app, branded as **GPTutor**, that provides AI-powered tutoring services. It leverages the VK platform to reach a wide audience, particularly focusing on Russian-speaking users. [Access it through or VK community](http://vk.com/gptutor).
- **Technology**: Built with React and Typescript, using the [vk-mini-apps-API](https://github.com/VKCOM/vk-mini-apps-api) for seamless integration with VK.
- **Setup**: Detailed setup instructions can be found in the [GPTutor README](https://github.com/deep-assistant/GPTutor/blob/main/README.md).

## Contributing
We welcome contributions to any of our projects! Please read our [contributing guidelines](https://github.com/deep-assistant/.github/blob/main/CONTRIBUTING.md) for more information on how to get involved.

## License
All projects under the Deep Assistant organization are licensed under the [Unlicense](https://unlicense.org/), allowing for maximum freedom in using and modifying the code.

---

Thank you for visiting our organization! For more information, please explore the individual repositories or contact us via GitHub issues.
