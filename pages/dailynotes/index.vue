<template>
  <main>
    <section v-if="posts" class="w-full max-w-5xl mx-auto">
      <h1 class="title">Dailynotes</h1>
      <posts post-type="dailynotes" :amount="10" />
    </section>
  </main>
</template>

<script>
export default {
  async asyncData({ $content, error }) {
    let posts;
    try {
      posts = await $content("dailynotes").fetch();
    } catch (e) {
      error({ message: "Notes not found" });
    }
    return { posts };
  },
}
</script>
