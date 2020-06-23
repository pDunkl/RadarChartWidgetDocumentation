![Image of Promo](Resources/Promo.png)

<h1>Radar Chart Widget</h1>

|<img src="Resources/Thumbnail.png" alt="drawing" width="100"/>| <h2> Documentation for the Radar Chart Widget Plugin for Unreal Engine </h2>|
|---|---|


Available at the Marketplace: [will follow soon]

# Overview
<details>
<summary>Designer Settings</summary>

![Image of Designer Settings](Resources/Settings.png)

+ <details>
    <summary>Chart</summary>

    |Setting|Description|
    |---|---|
    |Keep Aspect Ratio:|True = Force the Chart to keep aspect ratio, calculated by the smallest size. </br> False = Stretch to fill.|
    |Scale:|Scale the Radius of the whole Shape. 2.f meaning the shape is the size of the clipping rect. Caution this does not respect the labels!|
    |Appearance:|Appearance Settings for the Base. See <a href="#FRadarChartAppearance">FRadarChartAppearance</a>|

</details>
</details>

## Structs




<details>
<summary><a name="FRadarChartAppearance">FRadarChartAppearance</a></summary>

|Type|Name|Description
|---|---|---|
|bool|Draw:|Show/Hide the complete Shape Layer, including the Outline and Pins.|
|bool|Draw Shape:|Show/Hide the Shape.|
|bool|Concentric UVs:|True: The UVs are layed out pointing towards the center, making it easy to create radial symmetry. <br>False: The UVs are layed out normally.|
|bool|Draw Outline:|Show/Hide the outline|
|bool|Draw Pins:|Show/Hide the Pins|
|ERadarChartBlendMode|BlendMode:|Set the BlendMode of the used Material. See [ERadarChartBlendMode](#ERadarChartBlendMode)|

</details>

<details>
<summary> FRadarChartSegment</summary>

|Setting|Description|
|---|---|
|Keep Aspect Ratio:|True = Force the Chart to keep aspect ratio, calculated by the smallest size. </br> False =Stretch to fill.|
|Scale: | Scale the Radius of the whole Shape. 2.0 meaning the shape is the size of the clipping rect. Caution this does not respect the labels!|
|Appearance: |Appearance Settings for the Base. See FRadarChartAppearance Struct|

</details>


## Enums
 <details>

### ERadarChartBlendMode
|Name|Description|
|---|---|
|Opaque:| Set the Material to Opaque, Render Opacity is not supported. Best perfomance, less overdraw.|
|Translucent:| Set the Material to Translucent, Render Opacity is supported. Use final Alpha defined by color as opacity.|
|Additive:| Set the Material to Additive, adds it's color to the underlaying Pixels.|

</details>



# Usage
<details>

</details>

## Tips
<details>

</details>
