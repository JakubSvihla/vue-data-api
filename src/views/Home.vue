<template>

  <div class="app">
    <div class="domains">
    <Domains
      :domains="domains"
      v-on:get-info="getInfo"

    />
    <button class="btn btn-reload" @click="reload">Reload</button>
    </div>
    <InfoDisplay
      :info="info"
      class="infoDisplay"
    />
  </div>

</template>

<script>
import Domains from '../components/Domains';
import InfoDisplay from '../components/InfoDisplay';
import axios from 'axios';



export default {
  name: 'Home',
  components: {
    Domains,
    InfoDisplay,
  },
  data() {
    return {
      domains: [],
      info: [],
      domainId: Number,
      pageId: Number,
    }
  },
  methods: {
    getInfo(domainId, pageId) {

      this.domainId = domainId;
      this.pageId = pageId;

      axios({
        method: 'get',
        url: `https://www.ipushpull.com/api/1.0/domains/id/${domainId}/page_content/id/${pageId}/`,
      })
      .then(res => {
        this.info = res.data.content.flat();
      })
      .catch(err => console.log(err));
    },
    reload() {
      this.getInfo(this.domainId, this.pageId)
    }
  },
  created() {
    axios.get('https://www.ipushpull.com/api/1.0/domain_page_access/')
      .then(res => {
        const domains = res.data.domains;
        return this.domains = domains;
      })
      .catch(err => console.log(err));
  }
}
</script>

<style>
  * {
    box-sizing: border-box;
    margin: 0;
    padding: 0;
  }

  body {
    font-family: Arial, Helvetica, sans-serif;
    line-height: 1.4;
  }

  .btn {
    padding: 5px 10px;
    background-color: #4287f5;
    border-radius: 3px;
    width: 180px;
  }

  .btn-reload {
    width: 100px;
  }

  .app {
    display: flex;
  }

  .domains,
  .infoDisplay {
    width: 50%;
  }
</style>
