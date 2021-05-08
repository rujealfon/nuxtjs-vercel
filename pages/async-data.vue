<template>
  <div>
    <h1>{{ post.data }}</h1>
    <!-- <p>{{ post.description }}</p> -->
  </div>
</template>

<script>
export default {
  async asyncData({ params, $http }) {
    // console.log(params)
    const post = await $http.$get(`https://reqres.in/api/users?delay=5`)

    // console.log(post)
    return { post }
  },
  data: () => ({
    post: null,
  }),
}
</script>
