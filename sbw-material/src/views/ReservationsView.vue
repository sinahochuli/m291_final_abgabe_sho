<template>
  <div class="home">
    <ReservationList />
  </div>
</template>

<script>
// @ is an alias to /src
import ReservationList from '@/components/ReservationList.vue'

export default {
  name: 'ReservationsView',

  components: {
    ReservationList,
  },
  methods: {
    async doReserve() {
      alert('reserve');
    }
  }
}
</script>
