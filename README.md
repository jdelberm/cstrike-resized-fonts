This mod resizes the fonts of the chat, center HUD and default text, setting a more appropiate size accordinly to what it used to be before the update of 18 february 2025 of Counter Strike Source, where font family got updated and was made scalable.

# Installation
1. Download and unzip the repository files. Keep them in the unzipped folder.
2. Place it in the following path: ``steamapps\common\Counter-Strike Source\cstrike\custom\``

# Customization

You will have to look for the nodes that represents the font settings of the different UI components. I updated the following ones:
- `/resource/ClientScheme.res`
  - `HudHintText`: this is the center HUD.
  - `Default`: HUD at the right falls under this node.
- `/resource/ChatScheme.res`
  -  `ChatFont`: self explanatory.

I.E.  `HudHintText` would show as follows:
```
{
  HudHintText {
    "1"
    {
      "name"        "Verdana"
      "tall"        "12"
      "weight"    "700"
      "yres"    "480 599"
    }
    "2"
    {
      "name"        "Verdana"
      "tall"        "13"
      "weight"    "700"
      "yres"    "600 767"
    }
  }
}
```
Notice the child nodes "1", "2" (there is up to 5 or even more in some cases) and their attribute `yres`. This is the vertical resolution. You have to modify the child node according to your resolution in game. 

__Example:__ if you play at 800 x 600, you will have to modify the `tall` attribute of the node `"2"`. Whenever you change this, you will have to restart the game to see the changes applied.

**Note: you can create as many child nodes as you want. You could also have one child node per resolution by limiting the `yres` range to the desired vertical resolution. Just make sure to not overlap the ranges and leaving always one pixel of margin (i.e. from `"yres" "1080 2159"` to `"yres" "2160 10000"`)*
