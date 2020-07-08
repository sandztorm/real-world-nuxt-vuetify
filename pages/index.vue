<template>
  <v-container>
    <v-row>
      <v-col>
        <h1>Events</h1>
        <event-card
          v-for="(event, index) in events"
          :key="index"
          :event="event"
          :data-index="index"
        ></event-card>
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
import { mapState } from 'vuex'
import EventCard from '@/components/EventCard.vue'

export default {
  components: { EventCard },
  async fetch({ store, error }) {
    try {
      await store.dispatch('events/fetchEvents')
    } catch (e) {
      error({
        statusCode: 503,
        message: 'Unable to fetch events at this time. Please try again.',
      })
    }
  },
  computed: mapState({
    events: (state) => state.events.events,
  }),
  head() {
    return {
      title: 'Event Listing',
    }
  },
}
</script>
