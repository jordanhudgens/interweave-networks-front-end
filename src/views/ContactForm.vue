<template>
  <div>
    <h2>Contact Us</h2>
    <form @submit.prevent="submitContactForm">

      <input type="text" v-model="fullName" placeholder="Full Name">
      <input type="text" v-model="email" placeholder="Email">
      <textarea name="contactMessage" v-model="contactMessage" cols="30" rows="10" placeholder="Message"></textarea>

      <button type="submit">Send Message</button>
    </form>
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
      contactMessage: ''
    }
  },
  methods: {
    submitContactForm() {
      console.log(this.fullName);
      console.log(this.email);
      console.log(this.contactMessage);

      axios
        .post("https://interweave-networks-api.herokuapp.com/leads",
        {
          name: this.fullName,
          email: this.email,
          message: this.contactMessage,
          auth: {
            username: process.env.VUE_APP_API_KEY,
            password: process.env.VUE_APP_API_SECRET
          }
        })
        .then(response => {
          console.log(response.data);
          return response.data;
        })
        .catch(error => {
          console.log(error);
        })
    }
  }
}
</script>

