![Image of Promo](Resources/Promo.png)

<h1>Radar Chart Widget</h1>
<body>

|<img src="Resources/Thumbnail.png" alt="drawing" width="100"/>| <h2> Documentation for the Radar Chart Widget Plugin for Unreal Engine </h2>|
|---|---|


Available at the Marketplace: [will follow soon]

## Content </summary>
* 1\. [Overview](#Overview)
    * 1.1\. [Designer Settings](#DesignerSettings)
        * 1.1.1\. [Chart](#Chart)
        * 1.1.2\. [Segments](#Segments)
        * 1.1.3\. [Cuts](#Cuts)
        * 1.1.4\. [Dividers](#Dividers)
        * 1.1.5\. [Label Settings](#LabelSettings)
        * 1.1.6\. [Values](#Values)
        * 1.1.7\. [Perfomance](#Perfomance)
    * 1.2\. [Types](#Types)
        * 1.2.1\. [Structs](#Structs)
        * 1.2.2\. [Enums](#Enums)



# Overview

## DesignerSettings
<details>
<summary>Show Screenshot</summary>

![Image of Designer Settings](Resources/Settings.png)
</details>


### Chart
|Type|Setting|Description|
|---|---|---|
|bool|Keep Aspect Ratio:|True = Force the Chart to keep aspect ratio, calculated by the smallest size. </br> False = Stretch to fill.|
|float|Scale:|Scale the Radius of the whole Shape. 2.f meaning the shape is the size of the clipping rect. Caution this does not respect the labels!|
|[FRadarChartAppearance](#FRadarChartAppearance)|Appearance:|Appearance Settings for the Base. See [FRadarChartAppearance](#FRadarChartAppearance).|


### Segments
|Type|Setting|Description|
|---|---|---|
|TArray<[FRadarChartSegment](#FRadarChartSegment)>|Segments|Array of Segments, at least 3 Segments are required to draw a triangular shape. See [FRadarChartSegment](#FRadarChartSegment).|

### Cuts
The Lines going from the center to the outline.
|Type|Setting|Description|
|---|---|---|
|bool|Draw Cuts:|Show/Hide the cuts.|
|FLinearColor|Cuts Color:|The Color of the Cuts.|
|float|Cuts Thickness:|How thick the cuts should be drawn. Default = 1.f, but sometimes you need to increase it to something greater, because of antialiasing glitches.|
|uint8 (byte)|Cuts ZOrder Offset:| Adjust the Z Order, 0 = draw underneath the shape, 1 = above, any higher to draw above Value Layers, etc. slider max = 32, typed in max = 255.

### Dividers
The Rings dividing the Cuts
|Type|Setting|Description|
|---|---|---|
|bool|Draw Dividers:|Show/Hide the Dividers.|
|FLinearColor|Dividers Color:|The Color of the Dividers.|
|uint8 (byte)|Dividers Count:|How many dividers should be drawn, min = 1, slider max = 16, typed in max = 32.
|float|Dividers Thickness:|How thick the dividers should be drawn. Default = 1.f, but sometimes you need to increase it to something greater, because of antialiasing glitches.|
|uint8 (byte)|Dividers ZOrder Offset:| Adjust the Z Order, 0 = draw underneath the shape, 1 = above, any higher to draw above Value Layers, etc. slider max = 32, typed in max = 255.

### <a name="LabelSettings"></a>Label Settings
|Type|Setting|Description|
|---|---|---|
|bool|Draw Icons:|Show/Hide the Icons.|
|bool|Draw Labels:|Show/Hide the Text Labels.|
|bool|Draw SubLabels:|Show/Hide the SubLabels.|
|bool|Draw Label Background:|Show/Hide the Background behind the labels.|
|float|Distance:|Distance from the outline vertex to the middle of the Text Label. 0 = The TextLabel is centered above the corner.|
|float|Vertical Offset:| Offset all Labels up/down to accumulate for Icons/SubLabel positions. Use this to reposition the Labels if the vetical spacing is undesired.|
|[FRadarChartColorOverride](#FRadarChartColorOverride)|Icon Color:|ColorCoding for the Icon. See [FRadarChartColorOverride](#FRadarChartColorOverride).|
|FVector2D|Icon Size:|Size of the Icon. Default = <32.0, 32.0>|
|FVector2D|Icon Offset:|Used to offset the Icon from the Label center. Default = <0.0, -32.0>|
|[FRadarChartColorOverride](#FRadarChartColorOverride)|Label Color:|ColorCoding for the Text Label. See [FRadarChartColorOverride](#FRadarChartColorOverride).|
|FSlateFontInfo|LabelFont:|Font Settings for the text Label.|
|[FRadarChartColorOverride](#FRadarChartColorOverride)|Label Color:|ColorCoding for the SubLabel Text. See [FRadarChartColorOverride](#FRadarChartColorOverride).|
|FSlateFontInfo|SubLabelFont:|Font Settings for the SubLabel text.|
|FVector2D|SubLabel Offset:|Used to offset the SubLabel from the Label center. Default = <0.0, 32.0>|
|FSlateBrush|Background:|Brush to use as background for the .|
|[ERadarChartLabelBackgroundMethod](#ERadarChartLabelBackgroundMethod)|Background Wrap Method:|Which Wrapping policy to use. See [ERadarChartLabelBackgroundMethod](#ERadarChartLabelBackgroundMethod).|
|FVector2D|Background Padding:|Space between the background and chosen source.|
|FVector2D|Background Offset:|Offset of the background, only available when Method set to "Custom".|

### Values
|Type|Setting|Description|
|---|---|---|
|TArray<[FRadarChartValueData](#FRadarChartValueData)>|ValueLayers| Array of Value Data (Array of floats + [FRadarChartAppearance](FRadarChartAppearance)). Currently limited to a maximum of 4.</br> See [FRadarChartValueData](#FRadarChartValueData).|

### Perfomance
|Type|Setting|Description|
|---|---|---|
|bool|Wrap with Invalidation Panel|[Recommended] Wrap the Chart inside an SInvalidationPanel, so it gets cached. Saves performance! But needs to be invalidated if the Chart gets modified. See [InvalidatePanel](#InvalidatePanel)|

# Functions
## Invalidate Panel

## Types
### Structs
#### FRadarChartAppearance
|Type|Name|Description
|---|---|---|
|bool|Draw:|Show/Hide the complete Shape Layer, including the Outline and Pins.|
|bool|Draw Shape:|Show/Hide the Shape.|
|bool|Concentric UVs:|True: The UVs are layed out pointing towards the center, making it easy to create radial symmetry. <br>False: The UVs are layed out normally.|
|bool|Draw Outline:|Show/Hide the outline|
|bool|Draw Pins:|Show/Hide the Pins|
|ERadarChartBlendMode|BlendMode:|Set the BlendMode of the used Material. See [ERadarChartBlendMode](#ERadarChartBlendMode)|

#### FRadarChartValueData
|Type|Name|Description
|---|---|---|
|TArray<float>|Values:|Array of floats, amount must be equal to the segment array size. Values are normalized (0.0 - 1.0).|
|[FRadarChartAppearance](FRadarChartAppearance)|Appearance:|Appearance for this Layer. See [FRadarChartAppearance](FRadarChartAppearance)|

#### FRadarChartSegment
|Type|Name|Description
|---|---|---|
|FLinearColor|Color:|Color for current segment, useful for color coding all related information (Icon, Label, SubLabel, Pins, ...)|
|UObject*|Icon:|Icon for the current segment, can be a Texture or Material (Domain must be UI!)|
|FText|Label:|Text Label for the current segment, example:"ATK".|
|FText|SubLabel:|Usually set to the current value.|
|FVector2D|Offset:|Additional offset to adjust the position of the Icon, Label, SubLabel and Label Background for this segment only, at once.|

### Enums
#### ERadarChartBlendMode
|Name|Description|
|---|---|
|Opaque:| Set the Material to Opaque, Render Opacity is not supported. Best perfomance, less overdraw.|
|Translucent:| Set the Material to Translucent, Render Opacity is supported. Use final Alpha defined by color as opacity.|
|Additive:| Set the Material to Additive, adds it's color to the underlaying Pixels.|

#### ERadarChartColorOverride
|Name|Description|
|---|---|
|None:|Do not override, use the color set inside the segment.|
|Multiply:|Multiply the color with the segment color.|
|Overwrite:|Use this color instead of the segment color.|
|OverwriteAlphaOnly:|Use the segment color and the alpha of this one.|
|OverwriteHue:|Multiply the luminance of the segment color with the this color's Hue.|
|OverwriteHueAndAlpha:|Same as OverwriteHue but include Alpha.|
|Desaturate:|Desaturate the segment colorby the luminance of this color.|
|DesaturateAndAlpha:|Same as Desaturate but include Alpha.|

#### ERadarChartLabelBackgroundMethod
|Name|Description|
|---|---|
|Label:|Wrap around the text Label.|
|SubLabel:|Wrap around the SubLabel text.|
|Icon:|Wrap around the icon.|
|Custom:|Use Padding as Background Padding as size instead.|


## Tips
</body>
