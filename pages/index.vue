<template>
  <v-layout column justify-center>

    <v-flex xs12 sm8 md6>
      <v-card>
        <v-card-title class="headline">PURECLOUD Links</v-card-title>
        <v-card-text>
          <div class="links-grid">
            <template v-for="(link, i) in links">
              <div :key="`title-${i}`">{{ link.title }}</div>
              <a :key="`url-${i}`" :href="link.url" target="_blank">{{ link.url }}</a>
            </template>
          </div>
        </v-card-text>
      </v-card>
    </v-flex>

  </v-layout>
</template>

<script>
export default {
  name: 'index',
  data() {
    return {
      links: [
        { title: 'Platform API', url: 'https://developer.mypurecloud.com/api/rest/' },
        { title: 'Developer Tools', url: 'https://developer.mypurecloud.com/developer-tools/' },
        { title: 'Release Notes', url: 'https://help.mypurecloud.com/release-notes/' },
        { title: 'Release Notes / ja', url: 'https://ja.help.mypurecloud.com/release-notes/' },
        { title: 'PureCloud Github Repo', url: 'https://github.com/MyPureCloud' },
      ]
    }
  }
}
</script>


<style scoped>
.links-grid {
  display: grid;
  grid-template-columns: max-content 1fr;
  grid-gap: 1em;
  font-size: 1.2em;
}
</style>
