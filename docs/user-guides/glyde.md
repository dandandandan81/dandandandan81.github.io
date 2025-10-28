# Overview
Glyde is the web management interface for The ROOMNET Apple TV solution.
The interface provides configuration and management options for Apple TVs, areas and the balcony App.
It also provides metrics for TV channel usage for properties using the ROOMNET TV Application.


## Access
Access Glyde at [glyde.roomnet.com](https://glyde.roomnet.com)
A login is required and can be requested via your project manager or support. On first login you will be prompted to setup multi-factor-authentication

## Site Selector
If your login has access to multiple properties you will be presented with the site selector. Choose the required property. The sight selector can be accessed again by clicking the :material-sitemap-outline: icon at the top of the page. 

## Time Zone
Clicking the :material-cog: icon in the top right will allow you to change how times are shown throughout the gylde interface. The default behaviour will use the timezone of the device you are using. Selecting `Use Site's Timezone` will change this behaviour to show any date and. tiome based on the time zone of the property.  
This can be helpful when working acrross multiple properties especially if they are not in your location.

## Dashboard
On Login the dashboard is displayed. Overview data is displayed for devcies, areas, effusion server and PMS events.

### Devices
![devices](../assets/images/user-guides/device-metrics.png)
Reported status of devices is shown here.

- Total - All devices registered to this Property.
- Alerts - Number of devices that are not communicating with Glyde.
- Active - Number of activley communicating devices.
- Spare - Number of devices marked as spare.
- Quarantied - Number of devices marked with this status. This is typically used for devices that are under investigation.
- Missing - Number of devices marked as missing. Typically used for devices that cannot be located.
- Without Areas - Devices that have not been assigned to an area. If there are any devices without area this should be resolved quickly.

### Alert Metrics
![alert](../assets/images/user-guides/alert-metrics.png)
Provides a 30 day history of device alerts. Can be helpful in montoring the overall reliability of network connectivity and troubleshooting.

### Areas
![area](../assets/images/user-guides/area-metrics.png)
Totla areas configures and any that do not have devices assigned to them.
!!! info
    An Area is a container for devices. This is commonly a guest room, but could something like a gym or a public space.

### Effision metrics
![effusion](../assets/images/user-guides/effusion-metrics.png)
Reports the status of the MacMini(s) installed in the network. These MacMinis provide a local copy of assets and applications, ensuring the guest experience is as smooth as possible. 
In normal operation each section shoudl display a green tick.

### PMS
![pms](../assets/images/user-guides/pms-metrics.png)
The PMS interface is important in making sure all guest data is removed at the end of their stay. If there is any outage or odd behaviour devices may be reset to often or not at all. 
The line graph can be interacted with showing the number of events over the last 30 days. the section on the right gives a snapshot of the last events received and the timnes they occured.

## Devices
All devices assigned to the property can be viewed and managed from this section.
An overview af all devices is provided. 
Any devices with an Orange warning triagle are cont communicating with Glyde and require attention.
<br>
![devices](../assets/images/user-guides/devices.png)

Clicking on a device will reveal the details page
![devicedetails](../assets/images/user-guides/device-details.png)

This section provides detailed information and status details for a single device. There are also aspects of the device that can be configured.
- Cleardown - This will perform a complete wipe and rebuild of the device. All guest data will be removed including logins.
- Reset - A sime restart of the device in the room
- Delete - This will completley delete the device from glyde and your property. This is only availabe to site admins and should only be used under guidanve from a ROOMNET team member.

### settings
- Device Name - Sets the name of the device. This si the name Guests will see if they want to sue airplay. Typoically this would be the room number.









## Areas

## Activate

## Settings

## Tasks

## TV Metrics

Metrics data is only availabe when the ROOMNET TV application is used.
Metrics are collected anonymously and displayed as an overall for the property. The data displayed covers the last 30 days.

The data provided can be used to establish when TV channelsa are bieng watched and if there are any channels that are not being used. 
Channels that are not being used could be removed / replaced, making better usage of your hardware or subsciptions.


Overall viewing time is displayed at the top of the page. The green line shows collective hours viewed per day, the yellow an average viewing time based on the last 30 days. 

![tvgraph](../assets/images/user-guides/tv-metrics-graph.png)

Below the overall graph, several view are provided showing most and least used channels, usage by day and usage by hour of the day.

Each graph has a full report button. Clicking this will display a full list of channels available at the property and collective hours viewed over the last 30 days.

![tvmetrics](../assets/images/user-guides/tv-metrics-all.png)

## Balcony App
The Balcony section provides configuration for the Balcony App. This is covered in the [balcony](balcony.md) section