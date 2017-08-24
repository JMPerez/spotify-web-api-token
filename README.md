# Spotify Web API Token generator

A simple Node.js app that exposes an access token to use the Spotify Web API.

The server is suitable for applications that need an access token. If you are searching or looking up metadata you need to provide an access token [since January 2017](https://developer.spotify.com/news-stories/2017/01/27/removing-unauthenticated-calls-to-the-web-api/). The code in this repo implements the [OAuth's client credentials flow](https://developer.spotify.com/web-api/authorization-guide/#client-credentials-flow) to give you a token quickly.

Note, this doesn't deal with user login. For this you can use [spotify/web-api-auth-examples](https://github.com/spotify/web-api-auth-examples/tree/master/authorization_code) or see how this is implemented in [jmperez/c](https://github.com/JMPerez/c/blob/master/server/auth.js).

## Setting up

Install the dependencies running `npm i`.

You need to create a Spotify application to obtain the credentials. Go to https://developer.spotify.com/my-applications, log in with your Spotify account and create an application. Register http://localhost:3000 as your Redirect URI, and save.

Take the Client ID and Client Secret, and use them like this:

```bash
export SPOTIFY_CLIENT_ID=<your_client_id>
export SPOTIFY_CLIENT_SECRET=<your_client_secret>
npm start
```

Once running, make a request to http://localhost:3000/token to obtain a token. You will get a JSON response back, similar to this:

```js
{
  "token":"BQD-p11hAVqADUMM39t_no2bkaoVl6BhRRXdqlFUYLN3XRuZq-ZrGfC0T2CoN376g4wG6FZ4Pe3qEHx3ruijCQ"
}
```

You can change the port where the server is listening by exporting `PORT`. Eg, to run the server on http://localhost:8888:

```bash
export SPOTIFY_CLIENT_ID=<your_client_id>
export SPOTIFY_CLIENT_SECRET=<your_client_secret>
export PORT=8888
npm start
```

Make sure to update the Redirect URI, or register a new one, if you change the port or the host where the server is running.
