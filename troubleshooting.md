## Troubleshooting Plex Assistant

Whenever posting an issue always include the following info: 

* Any errors in your logs along with debug info (see below on how to enable debug)
* The method you're using (IFTTT, DialogFlow, HA Conversation)
* If the companion sensor is working `sensor.plex_assistant_devices`
* If you're able to use HA's built in Plex Integration without issue

## Enable debug logs for the component

Add the following to your configuration.yaml file, restart, ask plex assistant to do something, go to your logs and view full logs.

```yaml
logger:
  logs:
    custom_components.plex_assistant: debug
```
