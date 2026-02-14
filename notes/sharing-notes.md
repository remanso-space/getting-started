# Sharing notes on Remanso with ATProto

[ATProto](https://atproto.com/) is a protocol that lets you have control on your data.

1. Login to [Bluesky](https://bsky.social/about),
2. add [the github action](https://github.com/remanso-space/sequoia) with a new [app password](https://bsky.app/settings/app-passwords),
3. suffix the note you want to share with `.pub.md` and commit.

## The github action

```yaml
name: "Publish to the PDS"
on:
  push:
    branches: [main]

jobs:
  publish:
    runs-on: ubuntu-latest
    permissions:
      contents: write
    steps:
      - uses: actions/checkout@v4
      - uses: remanso-space/sequoia@main
        with:
          identifier: ${{ secrets.ATP_IDENTIFIER }}
          app-password: ${{ secrets.ATP_APP_PASSWORD }}
```
