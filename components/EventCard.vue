<template>
  <nuxt-link
    :to="'/event/' + event.id"
    style="text-decoration: none; color: inherit;"
  >
    <v-hover v-slot:default="{ hover }">
      <v-card
        v-ripple="{ center: true }"
        :elevation="hover ? 16 : 2"
        class="mx-auto"
        max-width="500"
      >
        <v-card-text>@{{ event.time }} on {{ parsedDate }}</v-card-text>
        <v-card-title>{{ event.title }}</v-card-title>
        <p class="display-1 text--primary">
          {{ event.attendees.length }} attending
        </p>
      </v-card>
    </v-hover>
  </nuxt-link>
</template>
<script>
export default {
  name: 'EventCard',
  props: {
    // eslint-disable-next-line vue/require-default-prop
    event: Object,
  },
  computed: {
    parsedDate() {
      const eventDate = new Date(this.event.date)
      return eventDate
    },
  },
}
</script>
