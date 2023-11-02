# Custom Clocks for Jivelite

This folder contains various custom clocks for use with Jivelite/Squeezelite on piCorePlayer with the Raspberry Pi official display.

## References

Custom Clock Wiki Page:

- https://wiki.slimdevices.com/index.php/Custom_Clock_applet.html

Official forum thread about this:

- https://forums.slimdevices.com/forum/user-forums/3rd-party-software/101656-custom-clock-for-jivelite-with-800x480-screen

## Prerequsites

Logitech Media Server:

- Custom Clock Helper installed - See: https://wiki.slimdevices.com/index.php/Custom_Clock_applet#Installation
  - Don't install the official Custom Clock app since it seems you have to use the version from below.
- SuperDateTime installed
  - Custom Clock uses SuperDateTime stuff to create and populate the clocks and weather icons
- License Manager
  - I don't think this is needed but it's on my working system so noting it. But from scratch, I would skip it and see if things work.

## How to Create/Edit/Use a Custom Clock and Related Notes

### Installation of Custom Clock

For this stuff to work, I had to do the following:

- Get the CustomClock code from here: https://sourceforge.net/projects/superdatetimewu/files/CC_STUFF/
  - This is a version for jivelite - don't install from official repo.
- Login to piCoreplayer box and do:

  ```bash
  ssh tc@PICOREPLAYERIP # passsword is piCore
  sudo chmod -R a+rwx ./CustomClock/
  ```

- Unzip and install the customclock directly on the piCoreplayer box:
  ```bash
    scp -r ./CUSTOMCLOCKFOLDER tc@PICOREPLAYERIP:/home/tc/.jivelite/userpath/applets
  ```

### Create a test custom clock

- Go to Logitech Media Server page
  - Advanced -> Custom Clock Helper
  - Select a simple clock from pull down.
  - Edit as follows:
    - CHANGE NAME to something like test-1
    - Select jivelite 480x800 and deselect other options
    - Click Apply

### Configure the clock on the piCoreplayer

- Go to piCoreplayer
  - Settings -> Screen -> Screensavers -> Custom Clock Settings
  - Select an empty Config slot
    - You should see a list of custom clocks
    - Select one and hit back button.
  - Back out to top menu and select Extras -> Custom Clock
    - Select the clock you configure above to test what it looks like.
  - If you are happy with it, go back to Settings -> Screen -> Screensavers -> When Off
    - Scroll down and select the Custom Clock you want.

### Customizing clocks

#### Getting a config file for a predefined clock

To make your own clock you need to start with a json config file.

You can COPY one of the files in this folder.

Or download one from here:

- https://wiki.slimdevices.com/index.php/Custom_Clock_styles.html

Or export one from the Logitech Media Server as follows ...

- Go to Logitech Media Server page
  - Advanced -> Custom Clock Helper
- Select a clock you want to use.
- Click the export checkbox and apply.
- This will download the json file.

#### Customizing the clock

The config file supports various types and values.

Start here to understand them:

- https://wiki.slimdevices.com/index.php/Custom_Clock_applet.html#Configuration_format

For the SuperDateTime related settings, the only place I can find them is by going to Logitech Media Server and going to the player tab and selecting the SuperDateTime item. This will show the various time and weather codes.

|See the following for info on Periods:

- https://forums.slimdevices.com/forum/user-forums/3rd-party-software/108838-announce-superdatetime-screensaver-v5-11-0-date-time-weather-sports-stocks?p=1654949#post1654949

If you look at one of the custom clocks in this repo, you'll see how they are used.

Tweak and install and test and repeat ....

#### Installing the Custom Clock

- Go to Logitech Media Server page
  - Advanced -> Custom Clock Helper
- Select the Import option
- Copy/paste the json into the text block.
  - If you are "updating" an existing clock, it's best to change the json and give it a new name.
- Click Apply
- Go to the section above, Configure the clock on the piCoreplayer.
