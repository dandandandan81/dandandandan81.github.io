# Samsung AU8000 Series Hospitality TV Setup Guide

!!! warning

    This guide is for the Hospitality AU800 Range for TVs. Model Numbers start with **HG** to denote they are hospitality versions. Check the TV is the hospitality version and not the retail version whoes model numbers begin **UN**


## Prerequisites

- This guide assumes a factory-fresh Samsung AU8000 Series Hospitality TV or one that has been factory reset
- A Samsung remote control is required
- For deploying the configuration to other Samsung AU8000 Series TVs, a blank USB stick formatted to FAT32 is needed

---

## Initial Setup Wizard

1. Power On TV
2. **Select Language Page**  - This step has no effect on the overall setup since the TV's functions are not used. However, this guide provides instructions only in English
3. **TV Installation Type**  - Select "Factory Menu" (the TV will automatically take you to the hospitality menu)

---

## Hospitality Menu (Part 1)

Work through the menu options below changing the settings to the given values. If a menu or option is not mentioned it shoulkd be left at its default value. 

### Power On
- **Power On Volume** – (Optional) Set a specific volume level for when the TV powers on
- **Max Volume** – (Optional) Set a limit for the maximum volume
- **Power On Source** – Set to HDMI1

### External Source
- **USB Pop-up Screen** – Disable

### Smart Service
- **Smart Features**
   - **Autorun Smart Hub** – Turn off
   - **Service Discovery** – Off

### Virtual Standby
- **Virtual Standby Mode** – On

Power the TV off and back on. It will power on to HDMI1

---

## TV Menus

Press the `Menu` button on the remote and adjust the following settings to the given values. As with above; if a menu or option is not mentioned it shoulkd be left at its default value. 

### Picture Menu
- **Expert Settings**
   - **Picture Clarity** – Off
   - **Contrast Enhancer** – Off

### General
- **External Device Manager**
   - **Input Signal Plus** – Enable for all inputs
- **Power and Energy Settings**
   - **Brightness Optimization** – Turn off
   - **Motion Lighting** – Turn off
   - **Screen Saver** – Turn off

---

## Hospitality Menu (Part 2)

Now that the settings are correct we need to lock the TV down so guests cannot change them.

To access the hospitality menu again, enter the following sequence on the remote:  
`Mute, 1, 1, 9, Enter` it may take a few attemps for this to work.

Again change the settings listed below, leaving other settings untouched.

### Menu OSD
- **Picture Menu Lock** – On
- **Menu Display** – Off
- **Channel Menu Display** – Off

### Security
- **Factory Lock** – On
   - **Password Setting** – Set an 8-digit password
   
!!! warning

    Make sure the password is securely logged and stored. If lost, only Samsung can unlock the TV settings and may require a site visit.


- **Password Input** – Enter your new password to verify it works. If incorrect, repeat the setup steps

---

## Testing

Power the TV off and on, then verify the following:

- The TV powers on directly to HDMI1
- A banner shows the TV input at the top, but no menus or other information are visible at the bottom
- Press the **Menu** button on the remote; you should not be able to access any TV settings

Setup is now complete.

---

## Configuration Cloning

To deploy the configuration to other Samsung AU8000 Series TVs, you can create a clone of the TV configuration on a USB stick formatted to FAT32.

!!! important

    The clone file is specific to the model **and** screen size of the TV. It is recommended to use one USB stick per model/screen size and store them safely for future use.

---

### Clone Creation Process

1. Insert the USB stick into the top USB socket
2. Enter the TV hospitality menu (`Mute, 1, 1, 9, Enter`)
3. Navigate to **Cloning** > **Clone TV to USB**

The TV will write the configuration to the USB stick. If the USB is not recognized, check the connection or try a different USB stick.

---

### Using the Clone to Configure a TV

#### For a Factory-New or Factory-Reset TV

1. Power on the TV
2. On the **Select Language** page, select your language (this does not affect setup)
3. On the **TV Installation Type** page, choose **Factory Menu**
4. In the factory menu, go to **Cloning**
5. Set **Settings Auto Initialize** to **On**
6. Select **Clone USB to TV** and follow the instructions

The TV will power off once the process is complete. Turn it back on and verify the following:

- The TV powers on directly to HDMI1
- A banner shows the TV input at the top, but no menus or information are visible at the bottom
- Press the **Menu** button on the remote; you should not be able to access any TV settings

Setup is complete.

#### For an Already Configured TV

1. Power on the TV
2. Enter the TV hospitality menu (`Mute, 1, 1, 9, Enter`)
3. Go to **Cloning**
4. Set **Settings Auto Initialize** to **On**
5. Select **Clone USB to TV** and follow the instructions

Power the TV off and on, and verify the same items as above. Setup is now complete.