# The End is Nigh: Shaders

A number of custom shaders for the game **The End is Nigh**, developed by
**Edmund McMillen** and **Tyler Glaiel**. These shaders can be used by modders
to create unique looking worlds and levels, with a variety of different effects.

A complete list of all the shaders with links to more info on their effects:

| Name                                                                                | File                              |
| :---------------------------------------------------------------------------------- | :-------------------------------- |
| [8-Bit](#8-bit)                                                                     | 8bit.shader                       |
| [8-Bit with Lighting](#8-bit-with-lighting)                                         | 8bit_lighting.shader              |
| [Scrolling Camera](#scrolling-camera)                                               | camerascroll.shader               |
| [Chromatic Aberration](#chromatic-aberration)                                       | chromatic.shader                  |
| [Chromatic Aberration with Pulse](#chromatic-abberation-with-pulse)                 | chromatic_pulse.shader            |
| [Color Change with Pulse](#color-change-with-pulse)                                 | colorpulse.shader                 |
| [Glowing Lava](#glowing-lava)                                                       | lavaglow.shader                   |
| [Glowing Lava with Heatwave](#glowing-lava-with-heatwave)                           | lavaglow_heatwave.shader          |
| [Glowing Lava with Lighting](#glowing-lava-with-lighting)                           | lavaglow_lighting.shader          |
| [Glowing Lava with Heatwave and Lighting](#glowing-lava-with-lighting-and-heatwave) | lavaglow_lighting_heatwave.shader |
| [Pixelate](#pixelate)                                                               | pixelate.shader                   |
| [Pixelate with Pulse](#pixelate-with-pulse)                                         | pixelate_pulse.shader             |
| [Red Alert](#red-alert)                                                             | redalert.shader                   |
| [Screenshake](#screenshake)                                                         | screenshake.shader                |
| [Static Pixelation](#static-pixelation)                                             | staticpixel.shader                |
| [Static Pixelation with Pulse](#static-pixelation-with-pulse)                       | staticpixel_pulse.shader          |
| [Vertical Flip](#vertical-flip)                                                     | verticalflip.shader               |

## 8-Bit

Limits the visible color range to create an 8-bit color palette effect.

**Variables:**
| Name                | Type  | Value                                         |
| :------------------ | :---- | :-------------------------------------------- |
| resolution          | float | The resolution of the color range.            |
| saturation          | float | The saturation of the resulting colors.       |
| mosaic_size         | vec2  | How large the on-screen pixels should be.     |

**Tileset:**
```
fx_shader_mid 8bit
midfx_graphics ShadeBox
midfx_layer 2
```

## 8-Bit with Lighting

Limits the visible color range to create an 8-bit color palette effect.

This shader also applies the lighting effect.

**Variables:**
| Name                | Type  | Value                                         |
| :------------------ | :---- | :-------------------------------------------- |
| light_color         | vec4  | Color of light above and on top of water.     |
| light_distance      | float | How far the glowing light will travel.        |
| light_resolution    | vec2  | The resolution of the lighting pixels.        |
| glow_strength       | float | How strong the glow effect should be.         |
| resolution          | float | The resolution of the color range.            |
| saturation          | float | The saturation of the resulting colors.       |
| mosaic_size         | vec2  | How large the on-screen pixels should be.     |

**Tileset:**
```
fx_shader_mid 8bit_lighting
midfx_graphics ShadeBox
midfx_layer 2
```

## Scrolling Camera

Roughly simulate a camera that follows the player around the level.

**How to Use:**
* Place the shader in the `shaders` folder and rename it `colormapped.shader`.
* Create a new level and set the camera bounds to be the size you want your scrolling camera to be.
* Make sure the camera bounds are completely outside of the actual level area.
* Place the camera bounds to the bottom-right so the player doesn't die for being off-screen.
* Use the level editor to create large enough levels to fulfill these requirements.

**Known Issues:**
* User interface elements will not be visible when playing like this.
* Most shaders are not compatible with the scrolling camera.
* The scrolling camera is global and cannot be turned off for specific levels.
* There are some issues with scrolling and it is not always reliable.

## Chromatic Aberration

Applies a chromatic aberration effect (splits the color channels).

**Variables:**
| Name                | Type  | Value                                         |
| :------------------ | :---- | :-------------------------------------------- |
| intensity           | vec2  | The intensity of the chromatic aberration.    |

**Tileset:**
```
fx_shader_mid chromatic
midfx_graphics SolidBox
midfx_layer 2
```

## Chromatic Aberration with Pulse

Pulses in and out of a chromatic aberration effect (splits the color channels).

**Variables:**
| Name                | Type  | Value                                         |
| :------------------ | :---- | :-------------------------------------------- |
| intensity           | vec2  | The intensity of the chromatic aberration.    |

**Tileset:**
```
fx_shader_mid chromatic_pulse
midfx_graphics SolidBox
midfx_layer 2
```

## Color Change with Pulse

Pulses between the current palette and a specific color.

**Variables:**
| Name                | Type  | Value                                         |
| :------------------ | :---- | :-------------------------------------------- |
| pulse_color         | vec4  | The color the shader should pulse towards.    |
| pulse_speed         | float | The speed at which the pulse will occur.      |
| max_color_intensity | float | How close the shader will get to pulse_color. |

**Tileset:**
```
fx_shader_mid colorpulse
midfx_graphics SolidBox
midfx_layer 2
```

## Glowing Lava

Applies an extremely intense glowing effect to lava.

**Variables:**
| Name                | Type  | Value                                         |
| :------------------ | :---- | :-------------------------------------------- |
| light_color         | vec4  | Color of light above and on top of water.     |
| light_distance      | float | How far the lighting will travel.             |
| glow_color          | vec4  | Color that white parts glow when near water.  |
| glow_strength       | float | How strong the glow effect should be.         |
| glow_threshold      | float | Green channel threshold to trigger glowing.   |
| glow_distance       | float | How far the glowing will travel.              |
| overexpose          | float | How much fully bright objects bleed.          |

**Tileset:**
```
fx_shader lavaripples
fx_shader_mid lavaglow
midfx_graphics ShadeBox
midfx_layer 2
```

## Glowing Lava with Heatwave

Applies an extremely intense glowing effect to lava.

This shader also applies the heatwave effect.

**Variables:**
| Name                | Type  | Value                                         |
| :------------------ | :---- | :-------------------------------------------- |
| light_color         | vec4  | Color of light above and on top of water.     |
| light_distance      | float | How far the lighting will travel.             |
| glow_color          | vec4  | Color that white parts glow when near water.  |
| glow_threshold      | float | Green channel threshold to trigger glowing.   |
| glow_distance       | float | How far the glowing will travel.              |
| overexpose          | float | How much fully bright objects bleed.          |

**Tileset:**
```
fx_shader lavaripples
fx_shader_mid lavaglow_heatwave
midfx_graphics ShadeBox
midfx_layer 2
```

## Glowing Lava with Lighting

Applies an extremely intense glowing effect to lava.

This shader also applies the lighting effect.

**Variables:**
| Name                | Type  | Value                                         |
| :------------------ | :---- | :-------------------------------------------- |
| light_color         | vec4  | Color of light above and on top of water.     |
| light_distance      | float | How far the lighting will travel.             |
| glow_color          | vec4  | Color that white parts glow when near water.  |
| glow_strength       | float | How strong the glow effect should be.         |
| glow_threshold      | float | Green channel threshold to trigger glowing.   |
| glow_distance       | float | How far the glowing will travel.              |
| overexpose          | float | How much fully bright objects bleed.          |

**Tileset:**
```
fx_shader lavaripples
fx_shader_mid lavaglow_lighting
midfx_graphics ShadeBox
midfx_layer 2
```

## Glowing Lava with Heatwave and Lighting

Applies an extremely intense glowing effect to lava.

This shader also applies the heatwave and lighting effects.

**Variables:**
| Name                | Type  | Value                                         |
| :------------------ | :---- | :-------------------------------------------- |
| light_color         | vec4  | Color of light above and on top of water.     |
| light_distance      | float | How far the lighting will travel.             |
| glow_color          | vec4  | Color that white parts glow when near water.  |
| glow_strength       | float | How strong the glow effect should be.         |
| glow_threshold      | float | Green channel threshold to trigger glowing.   |
| glow_distance       | float | How far the glowing will travel.              |
| overexpose          | float | How much fully bright objects bleed.          |

**Tileset:**
```
fx_shader lavaripples
fx_shader_mid lavaglow_lighting_heatwave
midfx_graphics ShadeBox
midfx_layer 2
```

## Pixelate

Pixelates the screen.

**Variables:**
| Name                | Type  | Value                                         |
| :------------------ | :---- | :-------------------------------------------- |
| pixel_density       | float | How much to pixelate the screen by.           |

**Tileset:**
```
fx_shader_mid pixelate
midfx_graphics SolidBox
midfx_layer 2
```

## Pixelate with Pulse

Pulses in and out of pixelating the screen.

**Variables:**
| Name                | Type  | Value                                         |
| :------------------ | :---- | :-------------------------------------------- |
| min_pixel_density   | float | The lower bound to pixelate by.               |
| max_pixel_density   | float | The upper bound to pixelate by.               |

**Tileset:**
```
fx_shader_mid pixelate_pulse
midfx_graphics SolidBox
midfx_layer 2
```

## Red Alert

Performs a slight chromatic aberration effect whilst shaking the screen and
pulsing to the color red (by default).

This shader also applies the lighting and glowing effects.

**Variables:**
| Name                | Type  | Value                                         |
| :------------------ | :---- | :-------------------------------------------- |
| light_color         | vec4  | Color of light above and on top of water.     |
| light_distance      | float | How far the glowing light will travel.        |
| glow_strength       | float | How strong the glow effect should be.         |
| pulse_color         | vec4  | The color the shader should pulse towards.    |
| pulse_speed         | float | The speed at which the pulse will occur.      |
| max_color_intensity | float | How close the shader will get to pulse_color. |
| chromatic_intensity | vec2  | The intensity of the chromatic aberration.    |
| shake_speed         | float | The speed at which to shake the screen.       |
| shake_intensity     | vec2  | The intensity of the screen shake.            |

**Tileset:**
```
fx_shader_mid redalert
midfx_graphics ShadeBox
midfx_layer 2
```

## Screenshake

Shakes the screen in random directions.

**Variables:**
| Name                | Type  | Value                                         |
| :------------------ | :---- | :-------------------------------------------- |
| speed               | float | The speed at which to shake the screen.       |
| intensity           | vec2  | The intensity of the screen shake.            |

**Tileset:**
```
fx_shader_mid screenshake
midfx_graphics SolidBox
midfx_layer 2
```

## Static Pixelation

Performs a slight chromatic aberration effect as well as a static effect whilst
pixelating the screen.

**Variables:**
| Name                | Type  | Value                                         |
| :------------------ | :---- | :-------------------------------------------- |
| pixel_density       | float | How much to pixelate the screen by.           |
| chromatic_intensity | vec2  | The intensity of the chromatic aberration.    |

**Tileset:**
```
fx_shader_mid staticpixel
midfx_graphics SolidBox
midfx_layer 2
```

## Static Pixelation with Pulse

Pulses in and out of performing a slight chromatic aberration effect as well as
a static effect whilst pixelating the screen.

**Variables:**
| Name                | Type  | Value                                         |
| :------------------ | :---- | :-------------------------------------------- |
| min_pixel_density   | float | The lower bound to pixelate by.               |
| max_pixel_density   | float | The upper bound to pixelate by.               |
| chromatic_intensity | vec2  | The intensity of the chromatic aberration.    |

**Tileset:**
```
fx_shader_mid staticpixel_pulse
midfx_graphics SolidBox
midfx_layer 2
```

## Vertical Flip

Flips the screen upside down (does not effect GUI elements).

**Tileset:**
```
fx_shader_mid verticalflip
midfx_graphics SolidBox
midfx_layer 2
```
