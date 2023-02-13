# BotWatchy

This is a watch face for the open E-Ink display smartwatch [Watchy](https://watchy.sqfmi.com/) inspired by the 'Legend of Zelda - Breath of the Wild'.

This is a fork from the original implementation (https://github.com/mehtmehtsen/BotWatchy) with improvements taken from other existing forks (https://github.com/Kuuchuu/BotWatchy-Fahrenheit and https://github.com/My-Key/BotWatchy): border decoration, step count, code improvements (not Fahrenheit display though!). It can be edited and uploaded in Arduino IDE.

## Features

- Compiles and uploads using Arduino IDE.
- Display battery state as hearts (with support for quarter hearts, just as in-game).
- Display steps as rupee count.
- Display week day and date. Even though there is nothing comparable in BotW's HUD, I need this data displayed.
- Display time (duh) just like in-game, but bigger and betterer (for readability).
- Display the weather as icons in a weather bar thingy, just like in-game (with the exception of an added icon for 'partly cloudy', as the game's icons were a bit vague on that for my taste). All weather data (including the one for the upcoming days) is requested from [openweathermap.org's one call API](https://openweathermap.org/api/one-call-api).
If there's no WiFi to get weather data from, the Watch Face will just keep on displaying the data it got the last time.
  - Current weather is shown as the first icon.
  - Tomorrow's weather is shown as the second icon.
  - Day after tomorrow's weather is shown as the third icon.
- Display temperature in a temperature indicator just as in-game. Displayed temperature range is constrained between -12°C and 32°C. 'Cold' zone begins at 0°C, 'hot' zone at 20°C. If your Watchy shows that the temperature is in those zones, make sure to switch into the right gear or boost your temperature resistance by consuming the appropriate food or medicine. With no WiFi, the temperature gotten from the last API call is displayed until there's a connection again. Default was to show the RTC temperature sensor's data, which only made sense for me if it's about 30°C outside.
- Display WiFi connectivity state using the Sheika sensor symbol. There's just 'on' or 'off'.

## Upload instructions

### Use Arduino IDE

This fork has moved things around so that it works with Arduino IDE.

### Your API key and location data

Copy `include/secrets_template.h`, into `include/secrets.h` and add your information to it.

### You want to change, modify or break the icons?

All used image assets are provided in the `assets` folder. Modify them to your heart's content and then use [image2cpp tool](http://javl.github.io/image2cpp/) to convert them. Make sure you tick 'Invert image colors', as I made the colors the wrong way around.  
I commented out the code related to the 'Array of all bitmaps for convenience' in the output code, as it was causing me inconvenience.

The UI font's original files are not included. See [here](https://www.reddit.com/r/zelda/comments/5txuba/breath_of_the_wild_ui_font/) for source. I let some online tool convert it to .ttf and then used [truetype2gfx](https://rop.nl/truetype2gfx/) to convert to C code.

## Thanks and contributions

### Zelda BOTW UI Kit by Hunter Paramore

Although I added some stuff on my own, I heavily relied on this amazing Zelda BotW UI Kit done in Figma. I was really happy I didn't have to create all the graphics I used from scratch. So thanks to some internet person apparently named 'Hunter Paramore'. Here's a link to their [Figma profile](https://www.figma.com/@hparamore).

### Calamity Sans

For the UI font, I was able to use 'Calamity Sans' by reddit user [75thTrombone](https://www.reddit.com/user/75thTrombone/). I'd love to credit them in some way, but all I know of is this [reddit post](https://www.reddit.com/r/zelda/comments/5txuba/breath_of_the_wild_ui_font/).
