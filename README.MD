# AI Slack Bot

This is a Slack bot that uses the [Slack API](https://api.slack.com/) to interact with the [Slack](https://slack.com/) messaging platform. It takes the message, or query from the user, then it uses the [Wit.ai](https://wit.ai/) API to extract the intent and entities from the message. The intent and entities are then used to determine the appropriate response from the bot. Once the response from the bot has been determined, the query is sent to Wolfram|Alpha to get the answer to the query. The answer is then sent back to the user.

## Getting Started

These instructions will get you a copy of the project up and running on your local machine for development and testing purposes.

### Prerequisites

* Go 1.1.2+
API Keys for the following APIs:
* [Slack API](https://api.slack.com/)
* [Wit.ai](https://wit.ai/)
* [Wolfram|Alpha](https://developer.wolframalpha.com/portal/apisignup.html)

### Slack API

For the Slack API, you will need to create an app. You can do this by going to [https://api.slack.com/apps](https://api.slack.com/apps). Once you have created the app, you will need to add the following features to the app:

* Enable Event Subscriptions
* Enable Socket Mode
* Subscribe to bot events: 
    * `message.channels` 
    * `message.groups` 
    * `message.im` 
    * `message.mpim`
    * `app_mention`
* Add the following Scopes:
    * `channels:history`
    * `channels:join`
    * `channels:manage`
    * `channels:read`
    * `chat:write`
    * `chat:write.customize`
    * `chat:write.public`
    * `commands`
    * `groups:history`
    * `groups:read`
    * `im:history`
    * `im:read`
    * `mpim:history`
    * `mpim:read`
    * `users:read`
  * `users:read.email`

### Wit.ai

For the Wit.ai API, you will need to create an app. You can do this by going to [https://wit.ai/](https://wit.ai/). Once you have created the app, you will need to add the following features to the app:

* Create a custom intent, name it something relevant to your app. For this app, I named it `wolfram`, as we are communicating with wolfram.
* Create an entity with the wolfram built-in entity. This will allow the bot to extract the query from the message.

### Wolfram|Alpha

For the Wolfram|Alpha API, you will need to create an app. You can do this by going to [https://developer.wolframalpha.com/portal/apisignup.html](https://developer.wolframalpha.com/portal/apisignup.html). Once you have created the app, you don't have to config anything, as we are using the free version of the API.

## Deployment

To deploy the bot, you will need to set API keys from the aforemetioned APIs as environment variables. You can do this by creating a `.env` file in the root of the project. The `.env` file should look like this:

    SLACK_BOT_TOKEN=YOUR_SLACK_BOT_TOKEN
    SLACK_APP_TOKEN=YOUR_SLACK_APP_TOKEN
    WIT_AI_TOKEN=WIT_AI_TOKEN
    WOLFRAM_APP_ID=YOUR_WOLFRAM_API_KEY

Once you have set the environment variables, you can run the bot by running the following command:

    go run main.go

Then, you can invite the bot to a channel by typing the following command in the channel:

    /invite @bot_name

Once the bot is invited to a channel, you can start sending messages to the bot. The bot will respond to any message that starts with `@bot_name`. For example, if the bot's name is `ai_bot`, then you can send the following message to the bot:

    @ai_bot who is the president of the Mexico?

The bot will respond with the following message:

        The current president of Mexico is Andrés Manuel López Obrador since December 1, 2018

That's all! Enjoy!
