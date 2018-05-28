<template>
  <div>
    <div v-if="contactSubmittedSuccessfully">
      <h2>{{ responseMessage }}</h2>
    </div>

    <div v-if="!contactSubmittedSuccessfully">
      <h2>Contact Us</h2>

      <div v-if="errorSubmittingContact">
        <h2>{{ responseMessage }}</h2>
      </div>

      <form @submit.prevent="submitContactForm" class="form-wrapper">

        <input type="text" v-model="fullName" placeholder="Full Name">
        <input type="text" v-model="email" placeholder="Email">
        <textarea name="contactMessage" v-model="contactMessage" cols="30" rows="10" placeholder="Message"></textarea>

        <button type="submit">Send Message</button>
      </form>
    </div>
  </div>
</template>

<script>
import axios from 'axios';

export default {
  name: 'ContactForm',
  data() {
    return {
      fullName: '',
      email: '',
      contactMessage: '',
      responseMessage: '',
      contactSubmittedSuccessfully: false,
      errorSubmittingContact: false,
    }
  },
  methods: {
    submitContactForm() {
      axios
        .post("https://interweave-networks-api.herokuapp.com/leads",
        {
          lead: {
            name: this.fullName,
            lead_email: this.email,
            lead_message: this.contactMessage,
          },
        },
        {
          auth: {
            username: process.env.VUE_APP_API_KEY,
            password: process.env.VUE_APP_API_SECRET
          }
        })
        .then(response => {
          console.log(response.data);
          this.errorSubmittingContact = false;
          this.contactSubmittedSuccessfully = true;
          this.responseMessage = 'Your form was submitted successfully, someone will contact you shortly.';
          return response.data;
        })
        .catch(error => {
          console.log(error);
          this.responseMessage = 'There was an error submitting the form, make sure you filled out all fields.';
          this.errorSubmittingContact = true;
        })
    }
  }
}
</script>

<style lang="scss" scoped>
.form-wrapper {
  display: grid;
  grid-template-columns: repeat(1fr);
  grid-gap: 20px;

  input {
    background-color: transparent;
    border-top: 1px transparent;
    border-right: 1px transparent;
    border-left: 1px transparent;
    border-bottom: 1px #42b983 solid;
    padding-bottom: 5px;
  }

  button {
    font-size: 1em;
    background-color: #42b983;
    border: #42b983 1px solid;
    color: #29394b;
  }

  input[type="text"] {
    font-size: 1.2em;
    color: #eaeaea;
  }

  textarea {
    background-color: transparent;
    font-size: 1.2em;
    color: #eaeaea;
    border: 1px solid #42b983;
    padding: 10px;
  }
}
</style>

