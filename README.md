# vue-popper
# [Vue Icons](https://kalimah-apps.github.io/vue-popper/)
[![npm](https://img.shields.io/npm/v/@kalimahapps/vue-popper.svg)](https://www.npmjs.com/package/@kalimahapps/vue-popper) 
[![npm](https://img.shields.io/npm/dt/@kalimahapps/vue-popper.svg)](https://www.npmjs.com/package/@kalimahapps/vue-popper)
![vue-3](https://img.shields.io/badge/vue-3-%2342b883)

A tooltip component for vue3 using popperjs

## Installation
### NPM
`npm install @kalimahapps/vue-popper`

### PNPM
`pnpm add @kalimahapps/vue-popper`

## Usage
### Local Registration
```vue
<template>
  <VuePopper hover :popper-options="popperOptions">
    <template #default>
        <button>Hover me</button>
    </template>

    <template #content>
        <div class="p-2">
            <p class="text-sm">This is a tooltip</p>
        </div>
    </template>
  </VuePopper>
</template>


<script lang="ts" setup>
import VuePopper from '@kalimahapps/vue-popper';

const popperOptions = {
	placement: 'top',
};
</script>

<style lang="scss" scoped></style>
```

### Global Registration
```vue
// your-component.vue
<template>
  <vue-popper hover :popper-options="popperOptions">
    <template #default>
        <button>Hover me</button>
    </template>

    <template #content>
        <div class="p-2">
            <p class="text-sm">This is a tooltip</p>
        </div>
    </template>
  </vue-popper>
</template>

<script lang="ts" setup>
const popperOptions = {
	placement: 'top',
};
</script>
```
    
```js
// main.js
import { createApp } from 'vue';
import VuePopper from '@kalimahapps/vue-popper';
import App from './App.vue';

const app = createApp(App);

app.component('VuePopper', VuePopper).mount('#app');
```

## Props
| Name                  | Default   | Description                                                                                     |
| --------------------- | --------- | ----------------------------------------------------------------------------------------------- |
| show-arrow            | `true`    | Whether to show the arrow                                                                       |
| hover                 | `false`   | Trigger element on hover                                                                        |
| disable-click-outside | `false`   | Disable clicking outside to close                                                               |
| open-delay            | `0`       | How many milliseconds to wait before opening the tooltip                                        |
| close-delay           | `0`       | How many milliseconds to wait before closing the tooltip                                        |
| interactive           | `false`   | Whether to interact with tooltip when hover is true                                             |
| popper-options        | See below | An object of popper options. This will be passed to the third argument of createPopper function |


## Default Popper Options
```js
{
  modifiers: [
    {
      name: 'offset',
      options: {
        offset: [0, 12],
      },
    },
    {
      name: 'preventOverflow',
      options: {
        padding: 8,
      },
    },
    {
      name: 'flip',
      options: {
        fallbackPlacements: ['top', 'bottom', 'left', 'right'],
      },
    },
  ],
}
```

## Slots
| Name    | Description                               |
| ------- | ----------------------------------------- |
| default | The element that will trigger the tooltip |
| content | The content of the tooltip                |

## Events
| Name   | Description                        |
| ------ | ---------------------------------- |
| opened | Emitted when the tooltip is opened |
| closed | Emitted when the tooltip is closed |

## Styling
To style the tooltip, you can customize the following css variables:
| Name                       | Default Value                                                                                                          | Description                                   |
| -------------------------- | ---------------------------------------------------------------------------------------------------------------------- | --------------------------------------------- |
| --vue-popper-bg            | `#fff`                                                                                                                 | Background color of the tooltip and the arrow |
| --vue-popper-border        | `0px solid transparent`                                                                                                | Border of the tooltip                         |
| --vue-popper-border-radius | `6px`                                                                                                                  | Border radius of the tooltip                  |
| --vue-popper-text-color    | `#000`                                                                                                                 | Text color of the tooltip                     |
| --vue-popper-shadow        | ` 0 0 20px 4px rgb(154 161 177 / 15%),    0 4px 80px -8px rgb(36 40 47 / 25%),    0 4px 4px -2px rgb(91 94 105 / 15%)` | Box shadow of the tooltip                     |
| --vue-popper-zindex        | `1000`                                                                                                                 | Z-index of the tooltip                        |
| --vue-popper-padding       | `0em`                                                                                                                  | Padding of the tooltip                        |

## Exposed Refs
| Name   | Description                                                             |
| ------ | ----------------------------------------------------------------------- |
| popper | The popper instance. You can use this to call popper's instance methods |

## Version History
- 1.0.0
  - Initial Release

## License

This project is licensed under the MIT License