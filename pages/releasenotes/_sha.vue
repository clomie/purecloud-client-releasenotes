<template>
  <div class="markdown-body" v-html="compiled" />
</template>

<script>
export default {
  async asyncData({ app, params }) {
    const contentOfReleaseNotes = await app.$axios.$get(
      `https://api.github.com/repos/MyPureCloud/platform-client-sdk-java/contents/releaseNotes.md?ref=${
      params.sha
      }`
    )
    const blob = await app.$axios.$get(contentOfReleaseNotes.git_url)
    const content = atob(blob.content.split('\n').join(''))
    return { content }
  },
  computed: {
    compiled() {
      return this.$md.render(this.content)
    }
  }
}
</script>

<style>
</style>
