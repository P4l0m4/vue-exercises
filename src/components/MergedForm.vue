<template>
  <article class="gArticle">
    <form class="gForm" ref="form" @submit.prevent="submit">
      <div :class="{ 'form-group--error': $v.name.$error }">
        <div class="gFormSubContainer">
          <label class="form__label">Name</label>
          <input
            class="gInput"
            name="name"
            placeholder="Paloma"
            v-model.trim="name"
          />
        </div>
      </div>
      <div class="error" v-if="!$v.name.required">Name is required</div>
      <div class="error" v-if="!$v.name.minLength">
        Name must have at least {{ $v.name.$params.minLength.min }} letters.
      </div>
      <div class="error" v-if="!$v.name.maxLength">
        Name must have at most {{ $v.name.$params.maxLength.max }} letters.
      </div>
      <div :class="{ 'form-group--error': $v.mail.$error }">
        <div class="gFormSubContainer">
          <label class="form__label">Email</label>
          <input
            class="gInput"
            placeholder="palomatejeda81@gmail.com"
            v-model.trim="mail"
            name="email"
          />
        </div>
      </div>
      <div class="error" v-if="!$v.mail.required">Email is required</div>
      <div class="error" v-if="!$v.mail.minLength">
        Email must have at least {{ $v.mail.$params.minLength.min }} letters.
      </div>
      <div class="error" v-if="!$v.mail.maxLength">
        Email must have at most {{ $v.mail.$params.maxLength.max }} letters.
      </div>
      <button
        class="gButton"
        type="submit"
        :disabled="submitStatus === 'PENDING'"
      >
        Submit!
      </button>
      <p class="typo__p" v-if="submitStatus === 'OK'">
        Thanks for your submission!
      </p>
      <p class="typo__p" v-if="submitStatus === 'ERROR'">
        Please fill the form correctly.
      </p>
      <p class="typo__p" v-if="submitStatus === 'PENDING'">Sending...</p>
    </form>
  </article>
</template>
<script>
import {
  required,
  minLength,
  maxLength,
  email,
} from "vuelidate/lib/validators";
import emailjs from "@emailjs/browser";

export default {
  name: "VuelidateForm",
  data() {
    return {
      name: "",
      mail: "",
      age: 0,
      submitStatus: null,
    };
  },
  validations: {
    name: {
      required,
      minLength: minLength(4),
      maxLength: maxLength(8),
    },
    mail: {
      required,
      minLength: minLength(6),
      maxLength: maxLength(40),
      email,
    },
  },

  methods: {
    submit() {
      this.$v.$touch();
      if (this.$v.$invalid) {
        this.submitStatus = "ERROR";
      } else {
        this.submitStatus = "PENDING";
        emailjs
          .sendForm(
            "service_f0ns79q",
            "template_wj3e9hd",
            this.$refs.form,
            "ZAG2PeOHvH8fTwjpW"
          )
          .then(() => {
            this.submitStatus = "OK";
          })
          .catch((error) => {
            console.log("FAILED...", error.text);
          });
      }
    },
  },

  //   methods: {
  //     async submit() {
  //       console.log("submit!");
  //       this.$v.$touch();
  //       if (this.$v.$invalid) {
  //         this.submitStatus = "ERROR";
  //       } else {
  //         this.submitStatus = "PENDING";
  //         try {
  //           const result = await emailjs.sendForm(
  //             "service_f0ns79q",
  //             "template_wj3e9hd",
  //             this.$refs.form,
  //             "ZAG2PeOHvH8fTwjpW"
  //           );
  //           console.log("SUCCESS!", result.text);
  //           this.submitStatus = "OK";
  //         } catch (error) {
  //           console.log("FAILED...", error.text);
  //         }
  //       }
  //     },
  //   },
};
</script>
