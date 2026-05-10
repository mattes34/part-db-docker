# part-db-docker

## Part-DB Update Manager via Watchtower

This compose setup includes a Watchtower companion container so Part-DB can trigger Docker image updates from the web UI (`System` → `Update Manager`).

Before starting the stack, add a strong shared token to your local `.env` file:

```env
WATCHTOWER_API_TOKEN=replace-with-a-long-random-secret
```

You can generate one with:

```bash
openssl rand -hex 32
```

The same token is passed to Part-DB as `WATCHTOWER_API_TOKEN` and to Watchtower as `WATCHTOWER_HTTP_API_TOKEN`. Watchtower is configured with `WATCHTOWER_LABEL_ENABLE=true`, so it only updates containers explicitly labelled with `com.centurylinklabs.watchtower.enable=true`.
