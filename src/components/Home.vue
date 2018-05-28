<template>
  <div class="home">
    <div @click="toggleContactForm" class="contact-button">
      {{ contactFormLinkText }}
    </div>

    <div v-show="showContactForm" class="contact-form-wrapper">
      <ContactForm />
    </div>

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
      showContactForm: false,
      contactFormLinkText: 'Contact us'
    }
  },
  components: {
    Companies,
    ContactForm
  },
  methods: {
    toggleContactForm() {
      this.showContactForm = !this.showContactForm;

      if (this.showContactForm) {
        this.contactFormLinkText = 'Close'
      } else {
        this.contactFormLinkText = 'Contact us'
      }
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

.contact-form-wrapper {
  position: absolute;
  right: 0;
  padding: 42px;
  background: #262626;
  border-top-left-radius: 5px;
  border-bottom-left-radius: 5px;
  width: 400px;
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
    margin-top: 20px;
  }

  .contact-form-wrapper {
    width: 80vw;
  }
}
</style>

