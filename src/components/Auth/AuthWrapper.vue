<template>
  <div>
    <template v-if="user">
      <slot></slot>
      <template v-if="isDev">
        <div class="block p-4">
          <button @click="logOut" class="px-3 py-1 font-bold rounded bg-gray-200 shadow">
            Logout
          </button>
        </div>
      </template>
    </template>
    <template v-else>
      <GoogleAuth></GoogleAuth>
    </template>
  </div>
</template>

<script lang='ts'>
import Vue from 'vue'

export default Vue.extend({
  computed: {
    user() {
      return this.$store.getters.isLoggedIn
    },
    isDev() {
      return process.env.NODE_ENV === 'development'
    }
  },
  methods: {
    async logOut() {
      await this.$fire.auth.signOut()
    }
  }
})
</script>

<style lang='scss' scoped>
</style>