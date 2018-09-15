<template>
  <v-layout column justify-center>

    <v-flex xs12 sm8 md6>
      <v-card>
        <v-card-title class="headline">Select the version from menu.</v-card-title>
      </v-card>
    </v-flex>

    <v-flex xs12 sm8 md6>
      <v-card>
        <v-card-title class="headline">PURECLOUD APIs</v-card-title>
        <v-card-text>
          <a href=" https://developer.mypurecloud.com/api/">https://developer.mypurecloud.com/api/</a>
        </v-card-text>
      </v-card>
    </v-flex>

  </v-layout>
</template>

<script>
import VueMarkdown from 'vue-markdown'

export default {
  components: {
    VueMarkdown
  }
}
</script>
