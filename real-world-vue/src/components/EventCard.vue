<template>
  <router-link
    class="event-links"
    :to="{ name: 'EventDetails', params: { id: event.id } }"
  >
    <div class="event-card">
      <span>
        <i class="icon">📆</i>
        <p>@{{ event.time }} on {{ event.date }}</p>
      </span>
      <h4>{{ event.title }}</h4>
    </div>
  </router-link>
</template>

<script>
export default {
  name: 'EventCard',
  props: {
    event: Object,
  },
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.event-card {
  padding: 22px;
  width: 320px;
  cursor: pointer;
  border: 1px solid #39495c;
  margin-bottom: 18px;
}
.icon {
  font-size: 32px;
}
.event-card:hover {
  transform: scale(1.01);
  box-shadow: 0 3px 12px 0 rgba(0, 0, 0, 0.2);
}

.event-links {
  color: #2c3e50;
  text-decoration: none;
}
</style>
