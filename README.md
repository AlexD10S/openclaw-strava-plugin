# @alexd10s/openclaw-strava

Turn OpenClaw into a Strava-aware running coach in minutes.

This community plugin connects your Strava account to OpenClaw so your agent can review activities, track trends, and answer training questions with your own data.

## What it provides

- `strava_auth_status` to check whether your Strava account is connected
- `strava_activities` to list recent activities
- `strava_activity_detail` to inspect a single activity in depth
- `strava_stats` to summarize recent, year-to-date, and all-time totals

## Why this plugin

- Personalized coaching context from your real Strava history
- Fast setup with OAuth linking through your OpenClaw gateway
- Practical tools for weekly reviews, progress checks, and activity deep dives

## Plugin page

- ClawHub: `https://clawhub.ai/plugins/%40alexd10s%2Fopenclaw-strava`

## Install

Recommended (ClawHub):

```bash
openclaw plugins install clawhub:@alexd10s/openclaw-strava
```

Alternative (npm spec):

```bash
openclaw plugins install @alexd10s/openclaw-strava
```

Local development install:

```bash
openclaw plugins install /path/to/openclaw-strava-plugin
```

## 60-second setup

1. Create a Strava API app at `https://www.strava.com/settings/api`.
2. Set the Authorization Callback Domain to `localhost` (or your gateway domain).
3. Configure credentials:

```bash
openclaw config set plugins.entries.strava.config.clientId "YOUR_CLIENT_ID"
openclaw config set plugins.entries.strava.config.clientSecret "YOUR_CLIENT_SECRET"
```

4. Restart your gateway.
5. Ask the agent for auth status, open the returned connect URL, and approve access.

## Detailed setup

1. Create a Strava API app at `https://www.strava.com/settings/api`.
2. Set the Authorization Callback Domain to `localhost` for local use, or your gateway hostname if you use a public tunnel/domain.
3. Configure the plugin:

```bash
openclaw config set plugins.entries.strava.config.clientId "YOUR_CLIENT_ID"
openclaw config set plugins.entries.strava.config.clientSecret "YOUR_CLIENT_SECRET"
```

4. Restart the gateway.
5. Ask the agent for Strava auth status. It will return a gateway connect URL. Open that URL in a browser already signed into your OpenClaw gateway to complete OAuth.

## Example prompts

- "Show my last 7 Strava activities and summarize pace trends."
- "Compare this week vs last week total distance and elevation."
- "Give me a short coaching note based on my last long run."

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
