# Manual

# Table of Contents
- [Terms](#terms)
- [Base Setting](#base-setting)
    - [UV Setting](#uv-setting)
- [Color](#color)
    - [Main Color](#main-color)
        - [Main Color](#main-color-1)
        - [Main Color 2nd / 3rd](#main-color-2nd--3rd)
        - [Alpha Mask](#alpha-mask)
    - [Shadow](#shadow)
    - [Emission](#emission)
- [Normal Map & Reflection](#normal-map--reflection)
    - [Normal Map](#normal-map)
    - [Reflections](#reflections)
        - [Reflection](#reflection)
        - [MatCap](#matcap)
        - [Rim Light](#rim-light)
- [Advanced](#advanced)
    - [Outline](#outline)
    - [Parallax](#parallax)
    - [DistanceFade](#distance-fade)
    - [AudioLink](#audiolink)
    - [Dissolve](#dissolve)
    - [Encryption](#encryption)
    - [Stencil](#stencil)
    - [Rendering](#rendering)
    - [Tessellation](#tessellation)
    - [Refraction](#refraction)
    - [Fur](#fur)
- [Optimization](#optimization)
    - [Optimization](#optimization-1)
    - [Shader Setting](#shader-setting)

<br/>

# Terms
|Name|Description|
|-|-|
|Material|The data that determines how we see things.|
|Texture|Images used for many things, such as determining the color of things.|
|UV|Data that determines the position of the texture to be applied.|
|Mask|Texture used to specify the area to be processed.|
|Normal Map|A texture that makes a surface appear to be uneven. It affects the appearance of shadows and gloss.|
|MatCap|Texture with light reflections drawn in.|
|Rim Light|Light that brightens only the outline of an object.|
|Stencil|Mask done on screen. You can draw eyebrows over hair.|

<br/>

# Base Setting
|Name|Description|
|-|-|
|Invisible|When this is turned on, the material will be hidden.|
|As Unlit|Disable lighting.|
|Rendering Mode|Allows you to change the transparency setting.|
|Cutoff|If the transparency drops below this value, the mesh will be clipped.|
|Cull Mode|Hide the specified surface.|
|Frip Backface Normal|Reverse backface lighting and other processes.|
|Backface Force Shadow|Intensity to force the back face to dark.|
|ZWrite|Whether to write depth. Basically, set it to on.|
|Vertex Light Strength|If you have multiple meshes, you can mitigate the difference in brightness between them by setting this property to 0.|
|Lower brightness limit|Limiting the darkness of a material by lighting|

<br/>

<details><summary>List of Rendering Mode</summary>

|Rendering Mode|Description|
|-|-|
|Opacue|Ignore transparency.|
|Cutout|Transparency is used, but translucent drawing is not possible.|
|Transparent|Transparency is used. If two transparent objects overlap, one of them may not be visible.|
|Refraction|[High-load] The transparent area will appear distorted.|
|Refraction Blur|[High-load] In addition to refraction, you can also create a frosted glass-like blur.|
|Fur|[High-load] Furry. In a spotlight, it becomes brighter than other materials.|
|Fur (Cutout)|[High-load] Furry. There is no brightness problem, but the appearance is rough.|
</details>

<br/>

## UV Setting
|Name|Description|
|-|-|
|Tiling|The number of loops in the UV.|
|Offset|The amount of displacement.|
|Angle|The angle of UV.|
|Scroll|The speed of UV movement.|
|Rotate|The speed of UV rotation.|

<br/>

# Color
## Main Color
### Main Color
|Name|Description|
|-|-|
|Texture|Specifies the texture. You can also use the color picker on the right to set the color.|
|Bake Alphamask|Applies a mask with a specified transparency to the texture.|
|Hue|Colour.|
|Saturation|Intensity of a color|
|Value|Lightness or darkness of a color.|
|Gamma|Emphasizes contrast.|
|Gradation Map|Color correct with gradient.|
|Bake|Export the color-corrected texture.|

### Main Color 2nd / 3rd
You can blend colors into the main color. This is the layer function in painting software.
|Name|Description|
|-|-|
|Texture|Specifies the texture. You can also specify a Gif image and click `Convert Gif` to animate it.|
|MSDF Texture|Sampling as [MSDF Texture](https://github.com/Chlumsky/msdfgen). The rendering will be similar to a vector image.|
|As Decal|When it is turned on, the layer is used as a decal.|
|Mask|Combine layers only in the area specified by the mask.|
|Enable Lighting|Apply the color of the light to rim light.|
|Blending Mode|How to combine layers. You can select Normal, Add, Screen, or Multiply.|
|Bake|Merges the layers into a single texture.|

<details><summary>Normal parameters</summary>

|Name|Description|
|-|-|
|Tiling|The number of loops in the UV|
|Offset|The amount of UV displacement.|
|Angle|The amount of UV angle shift.|
</details>

<details><summary>Parameters for decal</summary>

|Name|Description|
|-|-|
|Mirror Mode|Invert or display only one side. This setting is for cases where there is only one side of the UV.|
|Copy Mode|Invert or display only one side. This setting is for cases where the UV is symmetrical.|
|Position X/Y|Position of decals.|
|Scale X/Y|Scale of decals.|
|Angle|Angle of decals.|
|-|-|
|X/Y Frames|The number of frames on each axis.|
|Total Frames|Total number of frames.|
|FPS|Speed of animation.|
|Ratio X/Y|Ratio of whitespace to be set when there is whitespace to the right or bottom of the texture.|
|Fix Border|Increasing the value solves the problem when other frames extend beyond the top, bottom, left or right.|
</details>

-> [Dissolve Mode](#dissolve)

### Alpha Mask
|Name|Description|
|-|-|
|Alpha Mask|None: Disables the function / Replace: Replace the transparency of the main texture / Multiply: Multiplies the transparency of the main texture|
|Bake Alphamask|Applies a mask with a specified transparency to the texture.|

<br/>

## Shadow
|Name|Description|
|-|-|
|AO & Border|Range of shadow. You can specify an AO texture to change the ease of shadows.|
|Blur|Amount of shadow blur.|
|Mask & Strength|Strength of shadow. Shadows do not appear in the areas painted black by the mask.|
|1st/2nd Color|Color of shadow. You can specify a texture to override the color.|
|Main Color Power|Multiply the Main Color to emphasize the shadows.|
|Environment Strength|The intensity with which environment light affects the color of the shadow.|
|Border Color|Color of shadow border.|
|Border Range|Range of Border Color.|
|Receive Shadow|Receive shadows from other objects. It can look unnatural under a roof and is often better to turn it off.|

<br/>

## Emission
|Name|Description|
|-|-|
|Color|Color of Emission. You can set the UV by clicking on the triangle next to it.|
|Mask|Intensity and position of Emission. You can set the UV by clicking on the triangle next to it.|
|Blink Strength|Strength of blink.|
|Blink Type|Type of blink. Off:Smooth On:Step|
|Blink Speed|Speed of blink.|
|Blink Offset|Offset of blinking timing.|
|Gradation|Time variation of color.|
|Parallax Depth|Shifting UV according to viewing angle.|
|Fluorescence|Emission glows only when it is dark, but not in a completely dark space. Recommended for brightening the eyes in dark spaces.|

<br/>

# Normal Map & Reflection
## Normal Map
|Name|Description|
|-|-|
|Normal Map|Specifies the Normal Map.|
|Mask|Area and strength to apply normal map.|

<br/>

## Reflections
### Reflection
|Name|Description|
|-|-|
|Smoothness|Smoothness of the surface.|
|Metallic|Degree to which the material is close to metal.|
|Color|Color of reflection.|
|Specular Type|The appearance of light reflection.|
|Environment Reflections|Reflects environment light.|

### MatCap
|Name|Description|
|-|-|
|MatCap|Specifies the MatCap.|
|Mask|Area and strength to apply MatCap.|
|Enable Lighting|Apply the color of the light to MatCap.|
|Blending Mode|How to apply MatCap. You can select Normal, Add, Screen, or Multiply.|

### Rim Light
|Name|Description|
|-|-|
|Color|Color of rim light.|
|Border|Range of rim light.|
|Blur|Amount of rim light blur.|
|Fresnel Power|Sharpness of rim light.|
|Enable Lighting|Apply the color of the light to rim light.|
|Shadow Mask|Turn off rim light in the shadow.|

<br/>

# Advanced
## Outline
|Name|Description|
|-|-|
|Texture|Specifies the texture. You can also use the color picker on the right to set the color.|
|Hue|Colour.|
|Saturation|Intensity of a color|
|Value|Lightness or darkness of a color.|
|Gamma|Emphasizes contrast.|
|Bake|Export the color-corrected texture.|
|Mask & Width|Width of outline. The outline does not appear in the area painted black by the mask.|
|Fix Width|Correct width changes with distance.|
|Vertex R -> Width|Apply the R value of vertex color to the width.|
|Enable Lighting|Apply changes in brightness due to lighting.|

<br/>

## Parallax
|Name|Description|
|-|-|
|Parallax|Parallax map and its scale.|
|Offset|The threshold of parallax map.|

<br/>

## Distance Fade
|Name|Description|
|-|-|
|Color|Color of fade.|
|Start Distance|Distance to start the fade.|
|End Distance|Distance to end the fade.|
|Strength|Strength of fade.|

<br/>

## AudioLink
|Name|Description|
|-|-|
|UV Mode|The type of UV used to sample the audio effect.|
|Scale|Amount of timing shift according to UV.|
|Offset|Amount of timing shift.|
|Angle|The angle of UV.|
|Band|Bandwidth (pitch) to be sampled.|
|Mask|Mask texture that change the AudioLink process. (R:Delay G:Band B:Strength)|
|Apply to|Target to apply the effect to.|
|-|-|
|As Local|Use local texture instead of getting them from AudioLink.|
|Local Map|Local texture.|
|BPM|Speed of the song.|
|Notes|Number to be multiplied by BPM.|
|Offset|Amount of timing shift.|

<br/>

## Dissolve
|Name|Description|
|-|-|
|Dissolve|The type of effect.|
|Shape|The shape of effect.|
|Border|Range of effect.|
|Blur|Amount of effect blur.|
|Mask|(Mask mode) Mask texture of the effect.|
|Position|(UV / Position mode) Start position of the effect.|
|Vector|(UV / Position mode) Direction of movement of the effect.|
|Noise|Mask texture to add detail to effect.|
|Color|Color of effect.|

<br/>

## Encryption
[AvaterEncryption](https://github.com/lilxyzw/AvaterEncryption)
Decrypt the mesh from 4 keys.  
It can be used to prevent ripping, but not completely.
|Name|Description|
|-|-|
|Ignore Encryption|Turn this on if you do not want to encrypt the mesh.|
|Keys|Decryption keys.|

<br/>

## Stencil
If it is complicated and difficult to understand, you can use it without problems by understanding it as follows.

    Example: Draw eyebrows over hair
    Press "Set Writer" on the eyebrow material and "Set Reader" on the hair material.
    Match the "Ref" values of two materials.

|Name|Description|
|-|-|
|Ref|ID used for stencil. Decide whether or not to draw based on the ID.|
|ReadMask|Mask for the value of Ref before comparison.|
|WriteMask|Mask for the value to be written.|
|Comp|How to compare IDs. Material is drawn when the conditions are met.|
|Pass|Whether to rewrite the ID when the material is drawn.|
|Fail|Whether to rewrite the ID when the material is not drawn.|
|ZFail|Whether to rewrite the ID if there is an object in front of the material and it is not drawn, but the `Comp` condition is met.|
|Set Writer|Apply the material settings for writing the stencil|
|Set Reader|Apply the material settings for reading the stencil|
|Reset|Initializes the setting to no stencil.|

<br/>

## Rendering
This is a complex setting that is usually not changed. You can ignore them.
|Name|Description|
|-|-|
|Shader Type|Normal / Lite|
|Cull Mode|Hide the specified surface.|
|ZWrite|Whether to write depth. The value is larger at the back and smaller at the front.|
|ZTest|Method of comparing depth value. Material is drawn when the conditions are met.|
|Offset Factor|Increase or decrease the depth based on the screen coordinates.|
|Offset Units|Increase or decrease the depth.|
|SrcBlend|Value to be multiplied by the color calculated by the shader.|
|DstBlend|Value to be multiplied by the color already on the screen.|
|BlendOp|How to synthesize the calculation results. If you set it to anything other than `Add`, `SrcBlend` and `DstBlend` will be ignored.|
|ForwardAdd*|Setting used only when composing additional lights.|
|Enable GPU Instancing|Whether to perform GPU Instancing.|
|Render Queue|A number used to determine the order in which materials are drawn. The higher the value, the later it will be drawn.|

<br/>

## Tessellation
This is an experimental feature that smooths polygons when you get close to them. The load on high-poly models is very high, so it is best to use this only when you want to make a low-poly model look smooth.
|Name|Description|
|-|-|
|Threshold length|If the edge becomes longer than this value, split the polygon.|
|Strength|Strength of smoothing.|
|Shlink|Amount to shrink polygons. This is to compensate for the fact that the polygons will appear larger when smoothing.|
|Max Factor|Maximum number of divisions. The higher the value, the more load is applied.|

<br/>

## Refraction
|Name|Description|
|-|-|
|Strength|Strength to distort.|
|Fresnel|Distortion ease as a function of angle.|
|Refraction Color From Main|Apply main color to refraction color.|
|Color|Color of refraction.|

<br/>

## Fur
|Name|Description|
|-|-|
|Normal Map|Control fur vectors with Normal Map.|
|Vector|Vector of fur.|
|Length|Length of fur.|
|VertexColor -> Vector|Use vertex color as fur vector.|
|Gravity|Strength of gravity.|
|Noise|Noise texture used to generate fur.|
|Tiling|Fineness of the noise, or fineness of fur.|
|Offset|Offset of noise.|
|Mask|Deactivate the fur in the black area with the mask.|
|AO|Degree of shading applied to fur.|
|Layer|The amount of fur. The higher the value, the higher the density, but also the higher the load.|

<br/>

# Optimization
## Optimization
|Name|Description|
|-|-|
|Bake all layer|Merge the main color, color correction, and layers 2&3 into one texture. This will reduce the load and the change in appearance when you change to another shader.|
|Bake Color Shift|Export the color-corrected texture. This will reduce the change in appearance when you change to another shader.|
|Bake 2nd Layer|Merge the main color and 2nd layer into a single texture.|
|Bake 3rd Layer|Merge the main color and 3rd layer into a single texture.|
|Remove unused textures|Remove unused textures from the material.|
|Convert to lilToonLite|Convert the material to lilToonLite.|
|Convert to MToon(VRM)|Convert the material to MToon.|

<br/>

## Shader Setting
Features turned off here will be removed from the shader. By turning off unused features, you can reduce the size of your avatar while also reducing the load. When you place an avatar in a world, you need to match the shader settings specified by the world creator because the same settings are applied to all avatars placed in the world.