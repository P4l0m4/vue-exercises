<template>
  <main class="gMain">
    <h1>Test page</h1>
    <VuelidateForm /> <TestOnLinks />
  </main>
</template>

<script>
import TestOnLinks from "@/components/TestOnLinks.vue";
import VuelidateForm from "@/components/VuelidateForm.vue";
export default {
  components: {
    TestOnLinks,
    VuelidateForm,
  },
};
</script>

<style lang="scss" scoped></style>
