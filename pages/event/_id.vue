<template>
  <v-container>
    <v-card class="mx-auto" max-width="600">
      <v-card-text>@{{ event.time }} on {{ parsedDate }}</v-card-text>

      <v-card-title class="display-1">{{ event.title }}</v-card-title>
      <v-card-title>Organized by</v-card-title>
      <v-card-subtitle>{{ event.organizer }}</v-card-subtitle>
      <v-card-title>Category</v-card-title>
      <v-card-subtitle>{{ event.category }}</v-card-subtitle>
      <v-card-title>Location</v-card-title>
      <v-card-subtitle>{{ event.location }}</v-card-subtitle>
      <v-card-title>Event Details</v-card-title>
      <v-card-subtitle>{{ event.description }}</v-card-subtitle>
      <v-card-title>Attendees: {{ event.attendees.length }}</v-card-title>
      <v-card-subtitle
        v-for="(attendee, index) in event.attendees"
        :key="index"
        :index="index"
        >{{ attendee.name }}</v-card-subtitle
      >
    </v-card>
  </v-container>
</template>

<script>
import { mapState } from 'vuex'

export default {
  async fetch({ error, params, store }) {
    try {
      await store.dispatch('events/fetchEvent', params.id)
    } catch (e) {
      error({
        statusCode: 503,
        message: 'Unable to fetch the event at this time. Please try again.',
      })
    }
  },
  computed: {
    ...mapState({
      event: (state) => state.events.event,
    }),
    parsedDate() {
      const eventDate = new Date(this.event.date)
      return eventDate
    },
  },

  head() {
    return {
      title: this.event.title,
      meta: [
        {
          hid: 'description',
          name: 'description',
          content: 'What you need to know about ' + this.event.title,
        },
      ],
    }
  },
}
</script>
