<template>
  <div class='singlePage' :class="this.pageId === this.active ? 'active' : null">
    <button class="btn" @click="getInfo">{{name}}</button>
  </div>
</template>

<script>
export default {
  name: "SinglePage",
  props: {
    singlePage: Object,
    domainId: Number,
    active: Number,
  },
  data() {
    return {
      info: []
    };
  },
  methods: {
    getInfo() {
      this.$emit('get-info', this.domainId, this.pageId);
    },
  },
  computed: {
    name() {
      return this.singlePage.name;
    },
    pageId() {
      return this.singlePage.id
    }
  },
}
</script>

<style scoped>
  .singlePage {
    background: white;
    padding: 10px;
    border-bottom: 1px #ccc dotted;
  }

  .active {
    background-color: #00cc41;
  }
</style>

