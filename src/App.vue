<template>
  <div style="margin: 24px">
    <ButtonCounter />
    <ButtonJsx />
  </div>
</template>

<script>
import ButtonCounter from './components/ButtonCounter'
import ButtonJsx from './components/ButtonJsx'

export default {
  name: 'App',
  components: {
    ButtonCounter,
    ButtonJsx
  },
  data() {
    return {}
  }
}
</script>

<style>
</style>
