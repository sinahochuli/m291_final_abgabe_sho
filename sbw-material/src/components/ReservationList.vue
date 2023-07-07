<template>
  <table>
    <thead>
      <tr>
        <th>Lernpartner</th>
        <th>Material</th>
        <th>Von</th>
        <th>Bis</th>
        <th></th> <!-- Added an empty header for the delete button column -->
      </tr>
    </thead>
    <tbody>
      <tr v-for="reservation in reservations" :key="reservation.ID" :data-id="reservation.ID">
        <td>{{ reservation.Fullname }}</td>
        <td>{{ reservation.Equipment }}</td>
        <td>{{ reservation.Start }}</td>
        <td>{{ reservation.End }}</td>
        <td><button @click="deleteReservation(reservation.ID)">Delete</button></td> <!-- Updated the method name from "doDelete" to "deleteReservation" -->
      </tr>
    </tbody>
  </table>
</template>

<script setup>
import { store } from '@/store';
</script>

<script>
export default {
  name: "ReservationList",
  data() {
    return {
      reservations: [],
    }
  },
  created() {
    this.getReservations();
  },
  methods: {
    async getReservations() {
      const response = await fetch('https://projects.sbw.media/reservationview');
      this.reservations = await response.json();
    },
    async deleteReservation(resID) { // Updated the method name from "doDelete" to "deleteReservation"
      const response = await fetch(
        `https://projects.sbw.media/equipment_reservation/${resID}`,
        { method: "DELETE" }
      );
      const result = await response.json();
      if (result.result) {
        alert("Entry deleted");
      }
    }
  },
};
</script>

<style scoped>
table {
  border-collapse: collapse;
  margin: 0 auto;
}

td {
  text-align: left;
  padding: 0.5em 2em;
}
</style>
