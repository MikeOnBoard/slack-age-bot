# **Slack Age Bot**
A simple Slack bot to verify users' age by interacting with them in a Slack channel. Users provide their year of birth (YOB), and the bot processes the input, responding with the user's calculated age. This bot is designed to enhance engagement in Slack workspaces by adding an interactive, user-driven feature.

## **Project Structure**
```
slack-age-bot/
├── main.go
└── README.md
```
## **Features**
- **Age Verification**: Users input their year of birth, and the bot calculates and responds with their age.
- **Slack Integration**: The bot responds to messages in Slack channels and direct messages.
- **Interactive Conversations**: Works seamlessly with Slack's chat interface, engaging users in a dynamic way.
## **Installation and Setup**
### **1. Clone the Repository**
```bash
git clone https://github.com/MikeOnBoard/slack-age-bot.git
cd slack-age-bot
```
### **2. Set Up Your Environment**
Ensure that Go is installed on your machine. Then, resolve dependencies by running:
```bash
go mod tidy
```
### **3. Create a Slack App**
1. Visit the Slack API Dashboard and create a new app.

2. Enable Socket Mode in your app to allow real-time message reception.

3. Event Subscriptions:

- Add these subscriptions to enable event-driven interactions:
  - ``app_mention``: Triggered when the bot is mentioned in a message.
  - ``message.channels``: Triggered when new messages are posted in channels.
  - ``message.im``: Triggered in direct messages.
  - ``message.mpim``: Triggered in group direct messages.
4. OAuth & Permissions:

- Assign the following bot scopes for necessary permissions:
  - ``app_mentions:read``
  - ``channels:history``
  - ``channels:read``
  - ``chat:write``
  - ``chat:write.public``
  - ``im:history``
  - ``im:read``
  - ``im:write``
  - ``mpim:history``
  - ``mpim:read``
  - ``mpim:write``
5. Install the app in your workspace and get the bot token.

### **4. Configure Environment Variables**
Create a ``.env`` file in the project root with your Slack bot token:

```
SLACK_BOT_TOKEN=xoxb-...
```
### **5. Run the Applicatio**n
Run the bot using Go:

```bash
go run main.go
```
### 6. **Interact with the Bot**
Mention the bot in a channel or direct message to verify your age:

```css
@age-bot my yob is 1997
```
The bot will calculate your age and reply with a message indicating the calculated age.

## **File Overview**
### **``main.go``**
- Purpose: The core logic of the Slack Age Bot.
- Slack API Integration: Establishes the bot's connection to Slack via socket mode and listens for specific user messages.
- Message Handling: The bot listens for specific patterns in user input (e.g., "my yob is 1997"), processes the year of birth, and replies with the user's age.
- Error Handling: It includes basic error handling for potential issues with message formats or network errors.
### **Key Functions**:
- ``main()``: The main function initializes the bot, sets up the connection to Slack, and listens for events.
- ``handleMessage()``: Processes incoming messages, checks for the "YOB" input, and calculates the age based on the year of birth.
## **Usage Example**
A user types in a Slack channel or direct message:
```css
@age-bot "my yob is 1997"
```
The bot calculates the user's age and responds:
```css
Your age is 27
```
## **Conclusion**
This Slack Age Bot enhances workspace interactions by allowing users to quickly verify their age. Its simplicity, combined with Slack's messaging platform, makes it a fun and interactive tool that showcases the power of real-time bot development using Go and Slack's API.

The project serves as a good starting point for developers who want to explore Slack bot development and integrate interactive features into a communication platform.