# Lightwave2

Home Assistant (https://www.home-assistant.io/) component for controlling LightwaveRF (https://lightwaverf.com) devices with use of a Lightwave Link Plus hub. Controls both generation 1 ("Connect Series") and generation 2 ("Smart Series") devices. Does not work with gen1 hub.

Tested by me and working with:

- L21 1-gang Dimmer (2nd generation)
- LW430 3-gang Dimmer (1st generation)
- LW270 2-gang Power socket (1st generation)
- LW821 In-line relay (1st generation)
- LW934 Electric switch/thermostat (1st generation)

Tested by others:

- L22 2-gang Dimmer (2nd generation)
- Three-way relays (for controlling blinds/covers)

## Setup
There are two ways to set up:

#### 1. Manual
Copy all files from custom_components/lightwave2 to a `<ha_config_dir>/custom_components/lightwave2` directory. (i.e. you should have `<ha_config_dir>/custom_components/lightwave2/__init__.py`, `<ha_config_dir>/custom_components/lightwave2/switch.py` etc)

If you use this method then you'll need to keep an eye on this repository to check for updates.

#### 2. Using HACS
This component is also available through the Home Assistant Community Store HACS (https://hacs.netlify.com/)

If you use this method, your component will always update to the latest version. But you'll need to set up HACS first.
## Configuration

To use this component in your installation, add the following to your `configuration.yaml` file:

```yaml
lightwave2:
  username: example@example.co.uk
  password: hunter2
```

By default this uses a reverse engineered emulation of the Lightwave app. To use the offical API, add `backend: public`. There is no difference in functionality between the two implementations, but stability/responsiveness might differ depending on your network.

## Usage
Once configured this should then automatically add all switches, lights, thermostats and blinds/covers that are configured in your Lightwave app.

Generation 2 devices will have attributes `current_power_w` for current power usage and `lwrf_rgbColor` for the color of the LED.

The color of the LED can be changed using the service call `lightwave2.set_led_rgb`.


## Thanks
Credit to Warren Ashcroft whose code I used as a base https://github.com/washcroft/LightwaveRF-LinkPlus
