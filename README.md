# miro-webhooks-python

## Webhook Demo Youtube

![Webhooks-JavaScript](Getting-Started-With-Webhooks-JavaScript.png)

## Prerequisites
To complete this guide, you must:

* Set up a [Miro developer team](https://developers.miro.com/docs/the-developer-team).
* Have Python and pip installed.

### How to Start Locally

1. Clone this repo. 
2. Create a [developer app](https://developers.miro.com/docs/build-your-first-hello-world-app#step-2-create-your-app-in-miro).
3. [Configure your app](https://developers.miro.com/docs/build-your-first-hello-world-app#step-3-configure-your-app-in-miro). Rename .sample.env to [`.env`](.env) and then add in your client ID and client Secret. You can find clientId and clientSecret from the app settings page from your Miro app from developers.miro.com. Make sure to also add in a redirect URL. This needs to be `https` so localhost will not work. We recommend using [ngrok](https://ngrok.com/) for testing purposes, or another tool of your choice. You can run your local server on localhost:5000. Then you can run
`ngrok http 5000`. Ngrok will generate a forwarding address, and that can be your redirect URL. Make sure to add that redirectURL both within `.env` file and also within the app settings on Miro. 
4. [Install the app](https://developers.miro.com/docs/build-your-first-hello-world-app#step-4-install-your-app) on the team where the board you want to get events for is.
5. Save the `access_token`: you'll need it later.
6. Go to the root directory of this project.
7. Run `pip install -r requirements.txt` to install dependencies from the root of this project.
8. Run `flask --app app run` to start the server.

### How to Create a Webhook Subscription (to start getting events)

1. Go to the [create webhook subscription API page](https://developers.miro.com/reference/create-board-subscription) on developers.miro.com.
2. Add in your `access token` from step 5 in the previous section in the Authorization section in the top-right of the page.
3. Add in your boardId from the URL of the board you want to receive events from in the `Body Params` section. 
4. Add in the callbackUrl in the `Body Params` section.
5. Set status to `enabled` in the `Body Params` section.
6. Click on `Try It!` button below the Authorization section.

If all went well, you should see a 200. Then, you can create a sticky on your board, and you should see an event. 

Great job, you now know how to create a webhook subscription and receieve events! 