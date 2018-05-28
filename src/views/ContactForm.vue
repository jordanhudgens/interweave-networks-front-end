<template>
  <div>
    <h2>Contact Us</h2>
    <form @submit.prevent="submitContactForm">

      <input type="text" placeholder="Full Name">
      <input type="text" placeholder="Email">
      <textarea name="contactMessage" cols="30" rows="10" placeholder="Message"></textarea>

      <button type="submit">Send Message</button>
    </form>
  </div>
</template>

<script>
export default {
  name: 'ContactForm',
  methods: {
    submitContactForm() {
      console.log('Form Submittedd...');
    }
  }
}
</script>

