<template>
  <div class="home-view">
    <section class="section">
      <div class="field">
        Max: {{ maxNum }}
        <br>
        <input v-model.number="maxNum" type="range" min="10" max="100" step="10">
      </div>

      <div class="field">
        <b-checkbox v-model="isRandom">Randomize</b-checkbox>
      </div>

      <router-link class="button is-primary is-large is-outlined" to="/card">Start</router-link>
      <router-link class="button is-primary is-large is-outlined" to="/list">List</router-link>
    </section>
  </div>
</template>

<script lang="ts">
import Vue from 'vue'

export default Vue.extend({
  computed: {
    isRandom: {
      get(): boolean {
        return this.$store.state.isRandom
      },
      set(val: boolean) {
        this.$store.commit('update', { isRandom: val })
      },
    },
    maxNum: {
      get(): number {
        return this.$store.state.maxNum
      },
      set(val: number) {
        this.$store.commit('update', { maxNum: val })
      },
    },
  },
})
</script>

<style lang="scss" scoped>
input[type='range'] {
  width: 200px;
}
.button {
  display: block;
  margin: 1em auto;
  width: 200px;
}
</style>
