<template>
  <form class="gForm" ref="form" @submit.prevent="sendEmail">
    <label>Name</label>
    <input class="gInput" type="text" name="user_name" placeholder="Name" />
    <label>Email</label>
    <input class="gInput" type="email" name="user_email" placeholder="Email" />
    <label>Message</label>
    <textarea name="message"></textarea>
    <input class="gInput" type="submit" value="Send" />
  </form>
</template>

<script>
import emailjs from "@emailjs/browser";

export default {
  methods: {
    sendEmail() {
      emailjs
        .sendForm(
          "service_f0ns79q",
          "template_wj3e9hd",
          this.$refs.form,
          "ZAG2PeOHvH8fTwjpW"
        )
        .then(
          (result) => {
            console.log("SUCCESS!", result.text);
          },
          (error) => {
            console.log("FAILED...", error.text);
          }
        );
    },
  },
};
</script>
