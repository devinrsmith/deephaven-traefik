# deephaven-traefik

A Deephaven reverse-proxy setup using [traefik](https://github.com/traefik/traefik).

Currently, requires a [deephaven-core](https://github.com/deephaven/deephaven-core) server-jetty tar. Copy it into [server](./server/), then run:

```shell
docker compose build
docker compose up -d
```

Then, connect to [https://deephaven-foo.localhost](https://deephaven-foo.localhost) (you'll probably need to accept the self-signed certificate).
