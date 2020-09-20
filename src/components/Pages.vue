<template>
  <div>
    <div :key="singlePage.id" v-for="singlePage in pages">
      <SinglePage
        :singlePage="singlePage"
        :domainId="domainId"
        :active="active"
        v-on:get-info="getInfo"
      />
    </div>
  </div>
</template>

<script>
import SinglePage from './SinglePage';

export default {
  name: "Pages",
  components: {
    SinglePage,
  },
  methods: {
    getInfo(domainId, pageId) {
      this.$emit('get-info', domainId, pageId)
    },
  },
  props: {
    pages: Array,
    domainId: Number,
    pageId: Number,
    active: Number,
  }
}
</script>
