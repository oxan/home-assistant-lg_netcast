# `lg_netcast` integration with input source switching support

A patched version of Home Assistant's [lg_netcast][lg_netcast] integration, with support for switching input sources.

## Usage

- Install the integration by adding it as a custom repository to HACS, and restart Home Assistant.
- Set the debug level of the integration to debug in `configuration.yaml`:

    ```yaml
    logger:
    logs:
        custom_components.lg_netcast: debug
    ```

- Restart Home Assistant.
- Manually switch the TV to all (relevant) inputs, and watch for messages like the following in the Home Assistant logs.

    ```
    DEBUG (SyncWorker_1) [custom_components.lg_netcast.media_player] Currently active source: type=6, index=4, name=HDMI1
    DEBUG (SyncWorker_1) [custom_components.lg_netcast.media_player] Currently active source: type=6, index=5, name=HDMI2
    ```

- Configure the relevant input sources in `configuration.yaml` (you can customize the name of the inputs):

    ```yaml
    media_player:
    - platform: lg_netcast
      host: IP_ADDRESS
      sources:
      - name: HDMI1
        input_source_type: 6
        input_source_index: 4
      - name: HDMI2
        input_source_type: 6
        input_source_index: 5
    ```

- Remove the `logger` from the configuration, and restart Home Assistant again.

[lg_netcast]: https://www.home-assistant.io/integrations/lg_netcast/
