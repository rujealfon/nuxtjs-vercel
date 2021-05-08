<template>
  <p v-if="$fetchState.pending">Fetching mountains...</p>
  <p v-else-if="$fetchState.error">An error occurred :(</p>
  <div v-else>
    <h1>Nuxt Mountains</h1>
    <pre>{{ sample }}</pre>
    <ul>
      <li v-for="(mountain, index) of mountains" :key="index">
        {{ mountain.title }}
      </li>
    </ul>
    <button @click="$fetch">Refresh</button>
  </div>
</template>

<script>
export default {
  data() {
    return {
      mountains: [],
      sample: null,
    }
  },
  async fetch() {
    this.sample = await fetch(
      'https://reqres.in/api/users?delay=5'
    ).then((res) => res.json())

    this.mountains = await fetch(
      'https://api.nuxtjs.dev/mountains'
    ).then((res) => res.json())
  },
}
</script>
