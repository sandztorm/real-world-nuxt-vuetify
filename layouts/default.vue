<template>
  <v-app>
    <v-app-bar app color="primary" dense>
      <v-toolbar-title>
        <v-btn to="/" color="#fff" text rounded nuxt>Real World Events</v-btn>
      </v-toolbar-title>
      <v-spacer></v-spacer>
      <v-btn
        v-for="(link, index) in links"
        :key="index"
        :to="link.url"
        color="#fff"
        text
        rounded
        nuxt
        >{{ link.label }}</v-btn
      >
      <!-- <v-btn to="/event/create" color="#fff" text rounded nuxt>create</v-btn> -->
    </v-app-bar>

    <v-main><nuxt /></v-main>
    <v-footer color="primary lighten-1" padless>
      <v-row justify="center" no-gutters>
        <v-btn
          v-for="(link, index) in links"
          :key="index"
          :to="link.url"
          color="#fff"
          text
          rounded
          nuxt
          >{{ link.label }}</v-btn
        >
        <!-- <v-btn color="white" text rounded class="my-2" to="/" nuxt>
          List
        </v-btn>
        <v-btn color="white" text rounded class="my-2" to="/event/create" nuxt>
          Create
        </v-btn> -->
        <v-col class="primary lighten-2 py-4 text-center white--text" cols="12">
          {{ new Date().getFullYear() }} —
          <strong>Real World Events using Nuxt/Vuetify</strong>
        </v-col>
      </v-row>
    </v-footer>
  </v-app>
</template>

<script>
export default {
  data() {
    return {
      links: [
        {
          label: 'List',
          url: '/',
        },
        {
          label: 'Create',
          url: '/event/create',
        },
      ],
    }
  },
  head() {
    return {
      titleTemplate: '%s - Real World Events',
      meta: [
        {
          hid: 'description',
          name: 'description',
          content:
            'Where you can find all the events happening in your neighborhood',
        },
      ],
    }
  },
}
</script>
