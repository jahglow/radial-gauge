# radial-gauge

`radial-gauge` is an element providing an animated radial gauge (HTML5+CSS3) that may contain up to two gauge faces (secondary is nested inside primary one).
It's important to note, that a radial guage will display and animate only when 'reportalAppReady' event is fired. Generally that event is fired from app.js when all components are loaded

Make sure you include the contents of this style module (as-is or modified) in your theme file or main document to make the gauges display properly:

```html
    <style is="custom-style">
      radial-gauge {
        --radial-gauge-width:120px;
        --radial-gauge-rail-width:5px;
        --radial-gauge-secondary-rail-width:5px;
        --radial-gauge-secondary-offset: 0px;
        --radial-gauge-info-edge-offset: 5px;
      }
    </style>
```
Example for a single gauge with range at the top(default):
```html
    <radial-gauge value="76%" min="0" max="100" color="green" range></radial-gauge>
```
Example for a single gauge with range at the bottom:
```html
    <radial-gauge value="65%" min="-100" max="100" color="amber" range range-position="bottom"></radial-gauge>
```
Example for a double gauge with changed styles and a prefixed long value that adjusts font-size automatically:
```html
    <style is="custom-style">
      radial-gauge#fatOne{
        --radial-gauge-width: 150px;
        --radial-gauge-rail-width:16px;
        --radial-gauge-secondary-rail-width:8px;
        --radial-gauge-secondary-offset: -8px;
        --radial-gauge-info-edge-offset: 5px;
      }
    </style>
    <radial-gauge id="fatOne" value="84.078928" min="0" max="100" prefix="$" color="green" secondary-value="45" secondary-color="red"></radial-gauge>
```
Example for a gauge with top and bottom info, dynamic color calculation for primary gauge and a custom color for top-info:
```html
    <radial-gauge min="-100" max="100" range range-position="bottom" value="95" color="this.value<=69?'red':(this.value>=90?'green':'amber')" secondary-value="15" secondary-color="red" top-info="-44% " top-info-icon="undo" custom-top-info-color="#03A9F4" bottom-info="20%" bottom-info-icon="trending-up" bottom-info-color="grey"></radial-gauge>
```
### Styling

The following five custom properties included in your theme file change the appearance of the gauge:

Custom property | Description | Default
----------------|-------------|----------
`--radial-gauge-width` | Diameter of the primary gauge in pixels or other units (apart from %) | `120px`
`--radial-gauge-rail-width` | Width of the rail (primary gauge radial bar thickness) | `7px`
`--radial-gauge-secondary-rail-width` | Width of the rail for secondary gauge (inside the primary) | `7px`
`--radial-gauge-secondary-offset` | Gap between primary and secondary gauge  | `0px`
`--radial-gauge-info-edge-offset` | How far (from top or bottom respectively) the topInfo section and bottomInfor section are placed from the gauges' edge toward the main value. This setting might need tweaking when secondary gauge is used and its rail is very wide, so the top and bottom infos overlap it. | `5px`

The following custom properties and mixins are available for styling:

Custom property | Description | Default
----------------|-------------|----------
`--radial-gauge-rail` | Mixin for the gauge container (that has the grey rail underlying the primary gauge) | `{}`
`--radial-gauge-rail-background-color` | Rail background color | `#EEEEEE`
`--radial-gauge-info-circle` | Mixin for the round area inside the gauges which serves a container for all information | `{}`
`--radial-gauge-value` | Mixin for the main value | `{}`
`--radial-gauge-top-info` | Mixin for `topInfo` section | `{}`
`--radial-gauge-bottom-info` | Mixin for `bottomInfo` section | `{}`
`--radial-gauge-info-icon` | Mixin for icon styles for both info sections | `{--iron-icon-width:14px; --iron-icon-height:14px;}`
`--radial-gauge-range` | Mixin for both `min` and `max` range labels | `{}`

Shared custom properties:

Custom property | Description | Default
----------------|-------------|----------
`--conditional-formatting-red` | red color preset | `--paper-red-500`
`--conditional-formatting-amber` | amber color preset | `--paper-amber-500`
`--conditional-formatting-green` | green color preset | `--paper-green-500`
`--conditional-formatting-grey` | grey color preset | `--paper-grey-500`
