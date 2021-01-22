# Plex Assistant version ?.?.?
**Please, follow this guide when updating as this release has many improvements and new features, as well as breaking changes.**<br><br>

# Breaking Changes<br>

### Plex Server Config

Your Plex server is automatically retrieved from [Home Assistant's Plex integration](https://www.home-assistant.io/integrations/plex/). 
You need to have the Plex integration setup in order to use Plex Assistant. 
If you have more than one server setup use the new `server_name:` config option to select which one to use.<br>

This will help with configuration, support, requires less processing than the old method, and will allow for more improvements as Plex Assistant progresses.<br><br>

### Automation, Intent, Sensor

The automation, intent, intent script, and sensor are no longer required to be setup by the user. The component handles all of it now.<br>
This means you can safely remove them from HA. If you don't remove them it may cause issues and duplicate commands.

#### Remove these from your config:

<details>
  <summary><b>IFTTT Automation</b></summary>
  
```yaml
alias: Plex Assistant Automation
trigger:
- platform: event
  event_type: ifttt_webhook_received
  event_data:
    action: call_service
condition:
  condition: template
  value_template: "{{ trigger.event.data.service == 'plex_assistant.command' }}"
action:
- service: "{{ trigger.event.data.service }}"
  data:
    command: "{{ trigger.event.data.command }}"
```
  
</details>

<details>
  <summary><b>Intent</b></summary>

Keep `conversation:` and keep `intents:` if you have other intents.

```yaml
conversation: #### Keep this line
  intents:    #### and this one if you have other intents.
    Plex:
     # These trigger commands can be changed to suit your needs.
     - "Tell Plex to {command}"
     - "{command} with Plex"
```

</details>

<details>
  <summary><b>Intent Script</b></summary>
  
```yaml
intent_script:
  Plex:
    speech:
      text: "Command sent to Plex."
    action:
      - service: plex_assistant.command
        data:
          command: "{{command}}"
```
  
</details>
