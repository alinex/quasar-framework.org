title: Knob
---
Quasar Knob is another way of making the user select a Number value from a predefined range. With optional steps included. See demo.
<input type="hidden" data-fullpage-demo="forms/knob">

Works well with [QField](/components/field.html) for additional functionality such as a helper, error message placeholder and many others.

## Installation
Edit `/quasar.conf.js`:
```js
framework: {
  components: ['QKnob']
}
```

## Basic Usage

``` html
<q-knob
  v-model="model"
  :min="min"
  :max="max"
/>

<!-- With custom placeholder -->
<q-knob
  v-model="model"
  :min="min"
  :max="max"
  :placeholder="'$ ' + model"
/>

<!-- Disabled state -->
<q-knob
  disable
  v-model="model"
  :min="min"
  :max="max"
/>
```

## Vue Properties
Supports `v-model` which should be a Number.

| Vue Property | Type | Description |
| --- | --- | --- |
| `size` | String | CSS String determining the width and height of the Knob. Examples: "120px", "12rem". |
| `step` | Number | Number representing difference between two values that the model can take. Default: `1`. |
| `min` | Number | Minimum value that the model can take. |
| `max` | Number | Maximum value that the model can take. |
| `color` | String | One from [Quasar Color Palette](/components/color-palette.html). |
| `trackColor` | String | One from [Quasar Color Palette](/components/color-palette.html). |
| `lineWidth` | String | Line width of Knob. Default is '6px'. |
| `readonly` | Boolean | Sort of a "display" only mode. Model cannot be altered. |
| `disable` | Boolean | When set to `true` the model cannot be altered. |

## Vue Events
| Vue Event | Description |
| --- | --- |
| `@input(newVal)` | Triggered immediately on model value change. |
| `@change(newVal)` | Triggered on lazy model value change. |

## More Examples

### Lazy Input
Vue will soon supply the `.lazy` modifier for v-model on components too, but until then, you can use the longer equivalent form:
```html
<q-knob
  :value="model"
  @change="val => { model = val }"
  :min="min"
  :max="max"
/>
```

### Multi-colored with a Euro icon.
``` html
 <q-knob
  v-model="model"
  size="120px"
  style="font-size: 1.5rem"
  color="secondary"
  track-color="yellow-3"
  line-width="5px"
  :min="min"
  :max="max"
  :step="5"
>
  <q-icon class="on-left" name="euro_symbol" /> {{model}}
</q-knob>
```

### Read-only state (different than disabled, as the mouse pointer doesn't change).
``` html
<q-knob
  v-model="model"
  :min="min"
  :max="max"
  color="primary"
  readonly
>
  <q-icon class="on-left" name="volume_up" /> {{model}}
</q-knob>
```

### Using a [QField](/components/field.html) to highlight error state.
```html
<q-field
  label="Knob"
  icon="cake"
  helper="Touch to change"
  :error="knobHasError"
  error-label="Invalid value selected."
>
  <q-knob
    v-model="model"
    :min="min"
    :max="max"
  >
    <q-icon class="on-left" name="volume_up" /> {{model}}
  </q-knob>
</q-field>
```
