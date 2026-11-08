# paseo-web-ui

[Paseo](https://paseo.sh)'s web app, the one app.paseo.sh serves, as a
container image you can host yourself:

```sh
docker run --rm -p 8080:8080 ghcr.io/pfrybar/paseo-web-ui:0.15.3
```

The app comes from Paseo's own npm package, so each tag is the app of that
Paseo release. Use the tag matching the version your daemons run.

## Serving it

- Plain HTTP on port 8080, as a non-root user. Put TLS in front of it, such as
  a Kubernetes ingress.
- `/healthz` answers `ok`, for liveness and readiness probes.
- Files with a content hash in their name are cached for a year; `index.html`
  is revalidated on every load, so a new version shows up at once.

## Using it with your daemons

Point pairing links at your copy in each daemon's `~/.paseo/config.json`:

```json
{
  "app": { "baseUrl": "https://app.example.com" }
}
```

The app connects to daemons through their relay, as app.paseo.sh does.

## Tags

| Tag | What |
|---|---|
| `0.15.3` | the newest build of that Paseo version |
| `latest` | the newest build of `main` |
| `sha-<commit>` | the build of one commit |

## License

Paseo is licensed under the Apache License 2.0; its license is in the image at
`/licenses/paseo/LICENSE`.
