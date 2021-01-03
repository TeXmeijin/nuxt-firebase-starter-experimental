<template>
  <div class="max-w-full">
    <template v-if="isLoggedIn">
      <slot></slot>
      <template v-if="isDev">
        <div class="block p-4 fixed top-0 right-0">
          <button
            class="px-3 py-1 font-bold rounded bg-gray-200 shadow"
            @click="logOut"
          >
            Logout
          </button>
        </div>
      </template>
    </template>
    <template v-else>
      <slot name="logout"></slot>
    </template>
  </div>
</template>

<script lang="ts">
import Vue from 'vue'

export default Vue.extend({
  computed: {
    isLoggedIn() {
      return this.$store.getters.isLoggedIn
    },
    isDev() {
      return process.env.NODE_ENV === 'development'
    },
  },
  methods: {
    async logOut() {
      await this.$fire.auth.signOut()
    },
  },
})
</script>

<style lang="scss" scoped></style>
