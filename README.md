# NHLStandings-HA
Node-RED flow to create NHL standings sensors in HomeAssistant

![NHL Standings Flow](NHLStandings.png)

## Requirements
* node-red-contrib-home-assistant-websocket: https://flows.nodered.org/node/node-red-contrib-home-assistant-websocket
* node-red-contrib-loop-processing: https://flows.nodered.org/node/node-red-contrib-loop-processing
* hass-node-red integration (Install via HACS): https://github.com/zachowj/hass-node-red
* List Card by @iantrich (Install via HACS): https://github.com/iantrich/list-card

## Installation
If you don't yet have [node-red-contrib-home-assistant-websocket](https://flows.nodered.org/node/node-red-contrib-home-assistant-websocket) set up, you will need to configure that in Node-RED and also install the [hass-node-red integration](https://github.com/zachowj/hass-node-red) in Home Assistant.  It's definitely useful not only for this, but for many other automations. You also need the Node-RED loop processing contrib to easily handle arrays.

In Home Assistant, you will need [List Card by @iantrich](https://github.com/iantrich/list-card) installed in Home Assistant in order to display the information.  It's meant to use with the FeedParser integration, but will work with any sensor data as long as it's formatted reasonably and not multi-level, which is what a lot of fixing that the Node-RED flow does.

[lovelace-card-mod](https://github.com/thomasloven/lovelace-card-mod) would be useful for styling the tables so they are not so fugly.

The YAML file is for a complete dashboard.  You can paste it into the raw configuration editor on a new Lovelace dashboard. I plan on converting it to use Decluttering card at some pont to make it more manageable. 

![NHL Standings List Card](standings-list-card.png)

## Sensors

| entity                               | description                |
|--------------------------------------|----------------------------|
| sensor.nhl_standings                 | Current League Standings   |
| sensor.nhl_division_discover_central | Central Division standings |
| sensor.nhl_division_honda_west       | West Division standings    |
| sensor.nhl_division_scotia_north     | North Division standings   |
| sensor.nhl_division_mass_mutual_east | East Division standings    | 

## Troubleshotting
* If you've re-imported the flow, or cut and pasted parts, especially the entity nodes, you might have multiple entities, such as **nhl_standings_2**, so you'll have to remove or rename the orphaned entity and then renamed the duplicate to the original
* If you receive the error "unknown arrays" when you deploy the first time in Node-RED, you don't have [node-red-contrib-loop-processing](https://flows.nodered.org/node/node-red-contrib-loop-processing) installed.  Install it in your pallette.


## Credits
https://gitlab.com/dword4/nhlapi
