<template>
  <AuthWrapper>
    <h1>TOP Page</h1>
    Display when logged in.
    <template #logout>
      <p>Googleログイン</p>
      <GoogleAuth></GoogleAuth>
    </template>
  </AuthWrapper>
</template>

<script lang="ts">
import Vue from 'vue'

export default Vue.extend({})
</script>
