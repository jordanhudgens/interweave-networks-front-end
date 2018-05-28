<template>
  <div class="home">
    <div @click="toggleContactForm" class="contact-button">
      Contact us
    </div>
    <ContactForm v-show="showContactForm" />

    <img class="corp-logo" src="@/assets/logo.png">
    <h2>Featured Properties</h2>
    <Companies />

  </div>
</template>

<script>
import Companies from '@/components/Companies';
import ContactForm from '@/views/ContactForm';

export default {
  name: 'Home',
  data() {
    return {
      showContactForm: false
    }
  },
  components: {
    Companies,
    ContactForm
  },
  methods: {
    toggleContactForm() {
      this.showContactForm = !this.showContactForm;
    }
  }
}
</script>

<style lang="scss">
.contact-button {
  position: absolute;
  top: 0;
  right: 0;
  background-color: #42b983;
  color: white;
  width: 150px;
  height: 42px;
  display: flex;
  justify-content: center;
  align-items: center;
  font-weight: 900;
  transition: 0.3s;

  &:hover {
    cursor: pointer;
    background-color: #29394b;
    color: white;
  }
}


.corp-logo {
  width: 500px;
}

.nav {
  margin-top: 42px;
}

.nav-link {
  color: white;
  text-decoration: none;
  font-size: 1.25em;
  font-weight: 900;
  margin-left: 15px;
  margin-right: 15px;

  &:hover {
    color: #42b983;
  }
}

@media (max-width: 48em) {
  .corp-logo {
    width: 300px;
  }
}
</style>

