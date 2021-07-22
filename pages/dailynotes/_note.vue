<template>
  <main>
    	<!--Title-->
			<div class="font-sans">
				<p class="text-base md:text-sm text-green-500 font-bold">&lt; <a href="#" class="text-base md:text-sm text-green-500 font-bold no-underline hover:underline">BACK TO DAILYNOTES  <router-back class="block" /></a></p>
						<h1 class="font-bold font-sans break-normal text-gray-900 pt-6 pb-2 text-3xl md:text-4xl">{{ post.title }}</h1>
						<p class="text-sm md:text-base font-normal text-gray-600"  v-if="post.createdAt">Published {{ formatDate(post.createdAt) }}</p>
			</div>

   
       <nav class="mb-8" aria-label="go back">
       
      </nav>

      <article>
        <h5
          v-if="post.createdAt"
          class="inline-block py-1 px-2 my-2 bg-gray text-white text-sm font-medium rounded-sm whitespace-no-wrap"
        >{{ formatDate(post.createdAt) }}</h5>
        <h1 class="">{{ post.title }}</h1>
        <p class="mt-1 mb-4 text-primary-600 dark:text-primary-400">{{ post.description }}</p>
        <nuxt-content :document="post" />
      </article>
  </main>
</template>

<script>
export default {
   layout (context) {
    return 'blog'
  },
  async asyncData({ $content, params, error }) {
    let post;
    try {
      post = await $content("dailynotes", params.note).fetch();
    } catch (e) {
      error({ message: "Notes not found" });
    }
    return { post };
  },
  methods: {
    formatDate(dateString) {
      const date = new Date(dateString)
      return date.toLocaleDateString(process.env.lang) || ''
    }
  }
}
</script>
