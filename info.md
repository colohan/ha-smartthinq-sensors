# LG ThinQ Devices integration for HomeAssistant
A HomeAssistant custom integration to monitor and control LG devices using ThinQ API based on [WideQ project][wideq].<br/>
Supported devices are:
- Air Conditioner
- Air Purifier
- DishWasher
- Dryer
- Range 
- Refrigerator
- Styler
- Washer


**Important Version note:** 
1. From version 0.3.x component name changed from `smartthinq_washer` to `smartthinq_sensors`
If you are upgrading to version 0.3.x from previous version, you must **remove component configuration and uninstall component**
from Home Assistant before upgrade.<br/>

**Important**: The component will **not work if you have logged into the ThinQ application and registered your devices using a social network account** (google, facebook or amazon). In order to use the component you need to create a new independent LG account and make sure you log into the ThinQ app and associate your devices with it.
If during configuration you receive the message "No SmartThinQ devices found", probably your devices are still associated with the social network account. To solve the problem perform the following step:
- remove your devices from the ThinQ app
- logout from the app and login again with the independent LG account
- reconnect the devices in the app

**Important 2**: If you receive an "Invalid Credential" error during component configuration/startup, check in the LG mobile app if is requested to accept new Term Of Service.

**Note**: some device status may not be correctly detected, this depend on Washer model. I'm working to map all possible status developing the component in a way to allow to configure model option in the simplest possible way and provide update using Pull Requests. I will provide a guide on how update this information.<br/>

## Component configuration    
Once the component has been installed, you need to configure it in order to make it work.
There are two ways of doing so:
- Using the web interface (Lovelace) [**recommended**]
- Manually editing the configuration.yaml file

### Option A: Configuration using the web UI [recommended]
Simply add a new "integration" and look for "SmartThinQ LGE Sensors" among the proposed ones and
**follow setup worflow**.  (To do this:  1.  Go to "Settings->Devices & Services".  2.  Hit shift-reload in your browser (this is important!).  3. Click "+ Add Integration".  4.  Search for "SmartThinQ LGE Sensors".)<br/>

**Important**: use your country and language code: SmartThinQ accounts are associated with a specific locale, 
so be sure to use the country and language you originally created your account with. 
Reference for valid code:<br/>

- Country code: [ISO 3166-1 alpha-2 code][ISO-3166-1-alpha-2]<br/>
- Language code: [ISO 639-1 code][ISO-639-1]<br/>

### Option B: Configuration via editing configuration.yaml [deprecated - not possible from v0.5.4]
Follow these steps only if the previous configuration method did not work for you.<br/>
**Note**: with this configuration the integration will use APIv1 that cannot connect to new LG devices.
This configuration option is deprecated and is not possible starting from version 0.5.4<br/>

1. Enable the component by editing the configuration.yaml file (within the config directory as well).
Edit it by adding the following lines:
    ```
    smartthinq_sensors:
      token: my_smartthinq_token
      region: my_smartthinq_region #(ISO 3166-1 alpha-2, e.g. US)
      language: my_smartthinq_language #(ISO-639-1, e.g. en)
    ```

2. Reboot HomeAssistant

## Be nice!
If you like the component, why don't you support me by buying me a coffe?
It would certainly motivate me to further improve this work.

[![Buy me a coffe!](https://www.buymeacoffee.com/assets/img/custom_images/black_img.png)](https://www.buymeacoffee.com/ollo69)

Credits
-------

This component is developed by [Ollo69][ollo69] based on [WideQ API][wideq].<br/>
Original WideQ API was developed by [Adrian Sampson][adrian] under license [MIT][].

[ollo69]: https://github.com/ollo69
[wideq]: https://github.com/sampsyo/wideq
[adrian]: https://github.com/sampsyo
[mit]: https://opensource.org/licenses/MIT
[ISO-3166-1-alpha-2]: https://en.wikipedia.org/wiki/ISO_3166-2
[ISO-639-1]: https://en.wikipedia.org/wiki/List_of_ISO_639-1_codes
