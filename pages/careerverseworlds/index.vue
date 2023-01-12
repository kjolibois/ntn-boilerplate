<template>
  <main>
    <section v-if="posts" class="w-full max-w-5xl mx-auto">
      <h1 class="title">Careerverse worlds</h1>
      <posts post-type="worlds" :amount="20" />
    </section>
  </main>
</template>

<script>
export default {
  async asyncData({ $content, error }) {
    let posts;
    try {
      posts = await $content("CvWorlds").fetch();
    } catch (e) {
      error({ message: "worlds posts not found" });
    }
    return { posts };
  },
}
</script>
