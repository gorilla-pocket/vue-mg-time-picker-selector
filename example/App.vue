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
import 'bootstrap/dist/css/bootstrap.min.css'
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