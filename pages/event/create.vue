<template>
  <v-container>
    <v-row>
      <v-col>
        <h1>Create</h1>
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
export default {
  head() {
    return {
      title: 'Create an Event',
      meta: [
        {
          hid: 'description',
          name: 'description',
          content: 'You can create a new event in your neighborhood',
        },
      ],
    }
  },
}
</script>
