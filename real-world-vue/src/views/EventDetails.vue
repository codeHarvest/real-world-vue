<template>
  <div>
    <div class="event-detail" v-if="event">
      <span class="icon">📅</span>
      <h1>{{ event.title }}</h1>
      <p>{{ event.time }} on {{ event.date }} @ {{ event.location }}</p>
      <p>{{ event.description }}</p>
    </div>
  </div>
</template>

<script>
import EventService from '@/services/EventService'

export default {
  data() {
    return {
      event: null,
    }
  },
  props: ['id'],
  created() {
    EventService.getEvent(this.id)
      .then((response) => {
        this.event = response.data
      })
      .catch((error) => console.log(error))
  },
}
</script>

<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Luckiest+Guy&display=swap');

.event-detail {
  padding: 2rem;
  border: 1px solid black;
  border-radius: 5px;
  width: 50%;
  text-align: center;
  margin: 0 auto;
  line-height: 1.2;
}

h1 {
  font-size: 3rem;
  font-family: 'Luckiest Guy', cursive;
  letter-spacing: 3px;
}
p {
  font-size: 1.5rem;
}
.icon{
    font-size: 4rem;
}
</style>
