<template>
  <main>
    <section v-if="posts" class="w-full max-w-5xl mx-auto">
      <h1 class="title">Careerverse worlds</h1>
      <posts post-type="World" :amount="20" />
    </section>
  </main>
</template>

<script>
export default {
  async asyncData({ $content, error }) {
    let posts;
    try {
      posts = await $content("World").fetch();
    } catch (e) {
      error({ message: "Worlds posts not found" });
    }
    return { posts };
  },
}
</script>
