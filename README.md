This mod resizes the fonts of the chat, center HUD and default text, setting a more appropiate size accordingly to what it used to be before the update of 18 february 2025 of Counter Strike Source, where font family got updated and was made scalable.

| Resolution     |      Before      |  After  |
|:--------------:|:----------------:|:-------:|
| 1080 | ![20250226161256_1](https://github.com/user-attachments/assets/381465ee-89e5-4b7e-b6e7-42d21d33aa6e)| ![20250226162258_1](https://github.com/user-attachments/assets/95e84edd-748f-4ff8-8a8a-d771f927603d) |
| 4k   | ![20250226161122_1](https://github.com/user-attachments/assets/2c6d0f35-bb72-403b-a3f0-3cc75a1ab2c6)| ![20250226160826_1](https://github.com/user-attachments/assets/329aceed-d0df-40ed-9f65-b8167545539a) |

# Installation
1. Download and unzip the repository files. Keep them in the unzipped folder.
2. Place it in the following path: ``steamapps\common\Counter-Strike Source\cstrike\custom\``

# Customization

You will have to look for the nodes that represents the font settings of the different UI components and modify the `tall` attribute to change the font size. 

I updated the following ones:
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
Notice the child nodes `"1"`, `"2"` (there is up to 5 or even more in some cases) and their attribute `yres`. This is the vertical resolution. You have to modify the child node according to the range where your resolution in game falls.

__Example:__ if you play at 800 x 600, the vertical resolution(`600`) falls between the `yres` values of `600` and `767` in the node `"2"`, so you will have to modify the `tall` attribute in that child node for setting a different font size.

Whenever you change this, you will have to restart the game to see the changes applied.

*Note: you can create as many child nodes as you want. You could also have one child node per resolution by limiting the `yres` range to the desired vertical resolution. Just make sure to give to all the child nodes a sequential numeric name and to not overlap the `yres` range, leaving always one pixel of margin (i.e. from `"yres" "1080 2159"` to `"yres" "2160 10000"`)*
