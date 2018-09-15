<template>
  <v-app>
    <v-navigation-drawer v-model="drawer" fixed app>
      <v-list>
        <v-list-tile router :to="item.to" :key="i" v-for="(item, i) in items" exact>
          <v-list-tile-action>
            <v-icon v-html="item.icon"></v-icon>
          </v-list-tile-action>
          <v-list-tile-content>
            <v-list-tile-title>{{ item.version }}</v-list-tile-title>
            <v-list-tile-sub-title>{{ item.date }}</v-list-tile-sub-title>
          </v-list-tile-content>
        </v-list-tile>
      </v-list>
    </v-navigation-drawer>
    <v-toolbar dark fixed app color="cyan">
      <v-toolbar-side-icon @click="drawer = !drawer" />
      <v-toolbar-title v-text="title" />
      <v-spacer />
      <v-btn icon to="/">
        <v-icon>home</v-icon>
      </v-btn>
    </v-toolbar>
    <v-content>
      <v-container grid-list-md>
        <nuxt />
      </v-container>
    </v-content>
  </v-app>
</template>

<script>
export default {
  data() {
    return {
      title: 'PureCloud Client Release Notes',
      drawer: true,
      commits: [],
    }
  },
  computed: {
    items() {
      return this.commits.map(commit => ({
        icon: 'apps',
        version: commit.commit.message,
        date: commit.commit.committer.date,
        to: `/releasenotes/${commit.sha}`
      }))
    }
  },
  async mounted() {
    this.commits = await this.$axios.$get('https://api.github.com/repos/MyPureCloud/platform-client-sdk-java/commits')
  }
}
</script>
