# miro-webhooks-python

## App Setup Video (7 Minutes, JavaScript, but concepts are the similar to Python)
This video shows how to configure webhooks with JavaScript and Express.js. It should be
to the Python implementation.

Click on the thumbnail to [watch this video on YouTube](https://www.youtube.com/watch?v=sdwrsrriQNs).

[![Video](https://img.youtube.com/vi/sdwrsrriQNs/maxresdefault.jpg)](https://www.youtube.com/watch?v=sdwrsrriQNs)

## Prerequisites
To complete this guide, you must:

* Set up a [Miro developer team](https://developers.miro.com/docs/the-developer-team).
* Have Python and pip installed.

### How to Start Locally

1. Clone this repo. 
2. Create a [developer app](https://developers.miro.com/docs/build-your-first-hello-world-app#step-2-create-your-app-in-miro).
3. [Configure your app](https://developers.miro.com/docs/build-your-first-hello-world-app#step-3-configure-your-app-in-miro). Rename .sample.env to [`.env`](.env) and then add in your client ID and client Secret. You can find clientId and clientSecret from the app settings page from your Miro app from developers.miro.com. Make sure to also add in a redirect URL. This needs to be `https` so localhost will not work. We recommend using [ngrok](https://ngrok.com/) for testing purposes, or another tool of your choice. You can run your local server on localhost:5000. Then you can run
`ngrok http 5000`. Ngrok will generate a forwarding address, and that can be your redirect URL. Make sure to add that redirectURL both within `.env` file and also within the app settings on Miro.
4. Make sure to check `boards:read` as a scope, since it's needed to call the webhook API. 
5. [Install the app](https://developers.miro.com/docs/build-your-first-hello-world-app#step-4-install-your-app) on the team where the board you want to get events for is.
6. Save the `access_token`: you'll need it later.
7. Go to the root directory of this project.
8. Run `pip install -r requirements.txt` to install dependencies from the root of this project.
9. Run `flask --app app run` to start the server.

### How to Create a Webhook Subscription (to start getting events)

1. Go to the [create webhook subscription API page](https://developers.miro.com/reference/create-board-subscription) on developers.miro.com.
2. Add in your `access token` from step 5 in the previous section in the Authorization section in the top-right of the page.
3. Add in your boardId from the URL of the board you want to receive events from in the `Body Params` section. 
4. Add in the callbackUrl in the `Body Params` section.
5. Set status to `enabled` in the `Body Params` section.
6. Click on `Try It!` button below the Authorization section.

If all went well, you should see a 200. Then, you can create a sticky on your board, and you should see an event in your terminal. It should looks similar to the one below. (Some IDs were nulled for privacy).

```json
{'challenge': ''}
127.0.0.1 - - [25/Jul/2024 11:30:13] "POST / HTTP/1.1" 200 -
{'eventType': 'board_subscription', 'event': {'boardId': '', 'item': {'id': '', 'type': 'sticky_note', 'createdAt': '2024-07-25T09:30:20Z', 'createdBy': {'id': '', 'type': 'user'}, 'data': {'content': '', 'shape': 'square'}, 'geometry': {'width': 107.46000000000001, 'height': 123.12}, 'modifiedAt': '2024-07-25T09:30:20Z', 'modifiedBy': {'id': '', 'type': 'user'}, 'position': {'x': -12923.80732155303, 'y': -13565.86310249007, 'origin': 'center', 'relativeTo': 'canvas_center'}, 'style': {'fillColor': 'light_yellow', 'textAlign': 'CENTER', 'textAlignVertical': 'middle'}}, 'type': 'create'}, 'eventTime': '2024-07-25T09:30:20Z', 'appId': , 'users': []}
```

Great job, you now know how to create a webhook subscription and receieve events! 