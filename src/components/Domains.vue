<template>
  <div>
    <div
      :key="singleDomain.id"
      v-for="singleDomain in domains"
    >
      <SingleDomain
        :singleDomain="singleDomain"
        :active="active"
        v-on:get-info="getInfo"
      />
    </div>
  </div>
</template>

<script>
import SingleDomain from './SingleDomain.vue';


export default {
  name: "Domains",
  components: {
    SingleDomain,
  },
  data() {
    return {
      active: Number
    }
  },
  props: {
    domains: Array,
  },
  methods: {
    getInfo(domainId, pageId) {
      this.active = pageId;
      this.$emit('get-info', domainId, pageId)
    },
  }
}
</script>
