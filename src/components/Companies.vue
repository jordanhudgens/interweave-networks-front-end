<template>
  <div class="companies-wrapper">
    <h1>{{ someVar }}</h1>
    <div v-for="company in companyDataList" :key="company.title">
      {{ company.title }}
    </div>

  </div>
</template>

<script>
import axios from 'axios';

export default {
  name: 'Companies',
  data() {
    return {
      companyDataList: [],
      someVar: process.env.VUE_APP_SOME_VAR
    }
  },
  beforeMount() {
    this.getCompanies();
  },
  methods: {
    getCompanies() {
      axios
        .get("https://interweave-networks-api.herokuapp.com/companies",
        {
          auth: {
            username: process.env.VUE_APP_API_KEY,
            password: process.env.VUE_APP_API_SECRET
          }
        })
        .then(response => {
          console.log(response.data);
          this.companyDataList.push(...response.data);
          return response.data;
        })
        .catch(error => {
          console.log(error);
        })
    }
  }
}
</script>

<style scoped lang="scss">

</style>
