<template>
  <div class="infoDisplay">
    <div
      v-for="(value, index) in info"
      :key="`value-${index}`"
    >
      <p>{{value.value}}</p>
    </div>
  </div>
</template>

<script>

export default {
  name: "InfoDisplay",
  props: {
    info: Array
  },
}
</script>

<style scoped>
  .infoDisplay {
    /* background-color: #00cc41; */
    padding: 10px;
  }
</style>