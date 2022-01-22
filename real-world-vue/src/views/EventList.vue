<template>
  <div class="events">
    <event-card v-for="event in events" :key="event.id" :event="event" />
  </div>
</template>

<script>
// @ is an alias to /src
import EventCard from '@/components/EventCard.vue'
import EventService from '@/services/EventService'

export default {
  name: 'EventList',
  components: {
    EventCard,
  },
  data() {
    return {
      events: {},
    }
  },
  created() {
    EventService.getEvents()
      .then((response) => {
        this.events = response.data
      })
      .catch((error) => console.log(error))
  },
}
</script>

<style scoped>
.events {
  display: flex;
  align-items: center;
  flex-direction: column;
}
</style>
