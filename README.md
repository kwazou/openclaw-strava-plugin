# @kwazou/openclaw-strava

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

## Install

Install directly from GitHub:

```bash
openclaw plugins install git:github.com/kwazou/openclaw-strava-plugin@main
```

For a reproducible install, replace `main` with a release tag or commit hash.

Installing plugin code requires restarting the OpenClaw gateway.

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

## Publish to npm

The package is named `@kwazou/openclaw-strava`. After publishing it to npm, it can also be installed with:

```bash
openclaw plugins install npm:@kwazou/openclaw-strava
```

## Security notes

- OAuth tokens are stored with `0600` permissions.
- OAuth state nonces are used to prevent CSRF during account linking.
- The tool returns a gateway-authenticated connect URL instead of a raw Strava OAuth URL.

## Local development

```bash
pnpm install
pnpm build
pnpm test
pnpm typecheck
```
