<template>
  <vue-markdown :source="content" class="markdown-body" />
</template>

<script>
import VueMarkdown from 'vue-markdown'
export default {
  components: {
    VueMarkdown
  },
  async asyncData({ app, params }) {
    const contentOfReleaseNotes = await app.$axios.$get(
      `https://api.github.com/repos/MyPureCloud/platform-client-sdk-java/contents/releaseNotes.md?ref=${
      params.sha
      }`
    )
    const blob = await app.$axios.$get(contentOfReleaseNotes.git_url)
    const content = atob(blob.content.split('\n').join(''))
    return { content }
  }
}
</script>

<style>
</style>
