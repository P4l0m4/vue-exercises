<template>
  <div id="app">
    <nav class="gNav">
      <router-link class="gLink" to="/">Home</router-link> |
      <router-link class="gLink" to="/about">About</router-link> |
      <router-link class="gLink" to="/test">Tests</router-link>
    </nav>
    <router-view />
  </div>
</template>

<style lang="scss" src="@/global.scss">
@import url("@/global.scss");
</style>
