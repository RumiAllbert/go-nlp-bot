# AI Slack Bot

This is a Slack bot that uses the [Slack API](https://api.slack.com/) to interact with the [Slack](https://slack.com/) messaging platform. It takes the message, or query from the user, then it uses the [Wit.ai](https://wit.ai/) API to extract the intent and entities from the message. The intent and entities are then used to determine the appropriate response from the bot. Once the response from the bot has been determined, the query is sent to Wolfram|Alpha to get the answer to the query. The answer is then sent back to the user.

## Getting Started

These instructions will get you a copy of the project up and running on your local machine for development and testing purposes.

### Prerequisites
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