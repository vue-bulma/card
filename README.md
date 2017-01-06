# Card

Card component for Vue Bulma.

## Installation

```
$ npm install vue-bulma-card --save
```


## Examples

```vue
<template>
  <div>
    <base-card 
      :icon="'angle-right'"
      :title="'Github'" 
      :content="'Welcome to Github'">
      <card-footer-item slot="footer" :href="'https://github.com'">
        <span class="icon is-small">
          <i aria-hidden="true" class="fa fa-github"></i>
        </span>&nbsp;&nbsp;
        Github
      </card-footer-item>
    </base-card>
  </div>
</template>

<script>
import { BaseCard, CardFooterItem } from 'vue-bulma-card'

export default {
  components: {
    BaseCard,
    CardFooterItem
  }
}
</script>
```


## Badges

![](https://img.shields.io/badge/license-MIT-blue.svg)
![](https://img.shields.io/badge/status-dev-yellow.svg)

---
