# @alexd10s/openclaw-strava

Community Strava plugin for OpenClaw. It connects your Strava account to the gateway so the agent can read your activities and act as a running coach.

## What it provides

- `strava_auth_status` to check whether your Strava account is connected
- `strava_activities` to list recent activities
- `strava_activity_detail` to inspect a single activity in depth
- `strava_stats` to summarize recent, year-to-date, and all-time totals

## Install

After publishing to ClawHub:

```bash
openclaw plugins install clawhub:@alexd10s/openclaw-strava
```

Bare package installs also work once ClawHub has the package:

```bash
openclaw plugins install @alexd10s/openclaw-strava
```

For local testing before publish:

```bash
openclaw plugins install /path/to/openclaw-strava-plugin
```

## Setup

1. Create a Strava API app at `https://www.strava.com/settings/api`.
2. Set the Authorization Callback Domain to `localhost` for local use, or your gateway hostname if you use a public tunnel/domain.
3. Configure the plugin:

```bash
openclaw config set plugins.entries.strava.config.clientId "YOUR_CLIENT_ID"
openclaw config set plugins.entries.strava.config.clientSecret "YOUR_CLIENT_SECRET"
```

4. Restart the gateway.
5. Ask the agent for Strava auth status. It will return a gateway connect URL. Open that URL in a browser already signed into your OpenClaw gateway to complete OAuth.

## Publish to ClawHub

This scaffold assumes:

- package name: `@alexd10s/openclaw-strava`
- repo: `AlexD10S/openclaw-strava-plugin`

If you change either of those, update `package.json` before publishing.

```bash
npm i -g clawhub
clawhub login
clawhub package publish AlexD10S/openclaw-strava-plugin --dry-run
clawhub package publish AlexD10S/openclaw-strava-plugin
```

## Security notes

- OAuth tokens are stored with `0600` permissions.
- OAuth state nonces are used to prevent CSRF during account linking.
- The tool returns a gateway-authenticated connect URL instead of a raw Strava OAuth URL.

## Local development

```bash
pnpm install
pnpm test
pnpm typecheck
```
