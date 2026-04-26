# Launch Openfire action

An action for launching [Openfire](https://github.com/igniterealtime/Openfire), an XMPP server implementation, in the context of a Github Action workflow. It's not intended for anything production-facing, or even really user-facing. It's useful for CI-based short-lived actions that need an XMPP server.

## Inputs

### version

Version of Openfire to launch, in the form `a.b.c`, as seen in [Openfire Releases](https://github.com/igniterealtime/Openfire/releases).

example:

```yaml
      - name: Run Openfire
        uses: igniterealtime/launch-openfire-action@v1.2.0
        with:
          version: 4.9.0
```

### daily

Ignores any provided version, and loads the latest daily build of Openfire instead.

example:

```yaml
      - name: Run Openfire
        uses: igniterealtime/launch-openfire-action@v1.2.0
        with:
          daily: 'true'
```

### config

By default, the action launches with the demoboot config (the config file is [here](https://github.com/igniterealtime/Openfire/blob/main/distribution/src/conf/openfire-demoboot.xml), some docs [here](https://download.igniterealtime.org/openfire/docs/latest/documentation/client-minimal-working-example-smack.html#preparations)).

You can pass a different config file in to get alternative or additional config (e.g. adding additional configuration for plugins).

example:

```yaml
      - name: Run Openfire
        uses: igniterealtime/launch-openfire-action@v1.2.0
        with:
          config: ./my-config.xml
```

### logging

By default, Openfire is configured to log at INFO. This can be overridden for more or less granular information on Openfire's operation during the CI pipeline

example:

```yaml
      - name: Run Openfire
        uses: igniterealtime/launch-openfire-action@v1.2.0
        with:
          logLevel: debug
```