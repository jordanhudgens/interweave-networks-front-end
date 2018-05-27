<template>
  <div class="companies-wrapper">
    <div v-for="company in companyDataList" :key="company.title" class="company-wrapper">
      <CompanyTitle :title="company.title" />
      <CompanyLogo :logo="company.logo" />
      <CompanyDetails :companyDetails="company.description" />
    </div>
  </div>
</template>

<script>
import axios from 'axios';
import CompanyTitle from '@/views/company/CompanyTitle';
import CompanyLogo from '@/views/company/CompanyLogo';
import CompanyDetails from '@/views/company/CompanyDetails';

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
  components: {
    CompanyTitle,
    CompanyLogo,
    CompanyDetails
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
.companies-wrapper {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  grid-gap: 10px;
  padding: 100px;
}

.company-wrapper {
  background-color: #42b983;
  padding: 3em;
}

@media (max-width: 80em) {
  .companies-wrapper {
    grid-template-columns: repeat(2, 1fr);
    padding: 50px;
  }
}

@media (max-width: 48em) {
  .companies-wrapper {
    grid-template-columns: repeat(1, 1fr);
    padding: 4px;
  }
}
</style>
