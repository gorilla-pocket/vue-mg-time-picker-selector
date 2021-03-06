# vue-mg-time-picker-selector
vue-mg-time-picker-selector

## Installation

```
npm i vue-mg-time-picker-selector
```

## Usage

app.js

```javascript
import DateTimePickerSelector from 'vue-mg-time-picker-selector'
Vue.component('TimePickerSelector', TimeSelector)
```

Example:

```html
<template>
  <section class="container">
    <time-picker-selector v-model="time" :min-minute="minMinute" :max-minute="maxMinute"/>
    <div>time: {{time}}</div>
  </section>
</template>

<style lang="scss" scoped>
</style>

<script>
import TimePickerSelector from '../src/vue-mg-time-picker-selector'
export default {
  data() {
    return {
      time: '',
      minMinute: 1,
      maxMinute: 120,
    }
  },
  methods: {
    ///
  },
  components: {
    TimePickerSelector,
  },  
}
</script>
```

## License

MIT