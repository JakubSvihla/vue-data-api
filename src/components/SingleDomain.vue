<template>
  <div class="singleDomain">
    <p>Domain: {{name}}</p>
    <Pages
      :pages="pages"
      :domainId="domainId"
      :active="active"
      v-on:get-info="getInfo"
    />
  </div>
</template>

<script>
import Pages from './Pages';

export default {
  name: "SingleDomain",
  props: {
    singleDomain: Object,
    active: Number,
  },
  components: {
    Pages,
  },
  computed: {
    pages() {
      return this.singleDomain.current_user_domain_page_access.pages;
    },
    domainId() {
      return this.singleDomain.id
    },
    name() {
      return this.singleDomain.name
    }
  },
  methods: {
    getInfo(domainId, pageId) {
      this.$emit('get-info', domainId, pageId)
    },
  },
}
</script>

<style scoped>
  .singleDomain {
    background: #f4f4f4;
    padding: 10px;
    border-bottom: 1px #ccc dotted;
  }
</style>

