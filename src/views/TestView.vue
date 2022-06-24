<template>
  <main class="gMain">
    <h1>Test page</h1>
    <VuelidateForm /> <TestOnLinks /><EmailJs /><MergedForm />
  </main>
</template>

<script>
import TestOnLinks from "@/components/TestOnLinks.vue";
import VuelidateForm from "@/components/VuelidateForm.vue";
import EmailJs from "@/components/EmailJs.vue";
import MergedForm from "@/components/MergedForm.vue";
export default {
  components: {
    TestOnLinks,
    VuelidateForm,
    EmailJs,
    MergedForm,
  },
};
</script>

<style lang="scss" scoped></style>
