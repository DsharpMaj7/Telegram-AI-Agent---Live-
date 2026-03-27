A telegram chatbot using OpenAI chat model powered by n8n cloud. 

**Features**:
- Responds to user messages
- Uses GPT-4 for responses
- Triggered by Telegram messages from user
- Deployed via n8n cloud

**Setup Instructions**: Telegram > n8n > OpenAI > Telegram
- Open Telegram app
- Search BotFather and type in /newbot, hit enter
- Create bot name
- Create a username (can be same as bot name)
- BotFather will generate credentials/token access code
- Log into n8n Cloud
- Create new workflow
- Add Telegram Trigger Node
- Copy/Paste token access code into Telegram Trigger node (Updates: message)
- Click Execute workflow
- Send a message to your Telegram bot
- Confirm the node turns green (connection works)
- In n8n editor, click + on Telegram Trigger node, add AI Agent
- Add Chat Model, Open AI Chat Model
- Add OpenAI credentials > Go to https://platform.openai.com/settings/, click API Keys, click + Create new secret Key
- Copy and paste key into OpenAI Chat Model node
- Can change Model: From List, depending on the tier you are using
- In n8n editor, click + on AI Agent, add Telegram Send Message Node
- Set: Resource: Message, Operation: Send Message, drag Chat ID from input into parameters Chat ID, code: {{ $('Telegram Trigger').item.json.message.chat.id}}, drag Output from input into parameters Text, code: {{ $json.output }}
- Click Execute workflow, ensure everything turns green
- Publish workflow to activate workflow, otherwise it will be in test/manual mode
- Test, send a message in your new telegram chatbot, "What is the capital of Sweden?", you should receive a response from your bot.
