<template>
  <div>
    <img alt="logo" src="../assets/logo.png" />

    <div class="form">
      <LernpartnerSelect/>
      <MaterialSelect/>
      <label for="from">Von:</label>
      <input id="from" type="date" v-model="fromDate" />
      <label for="to">Bis:</label>
      <input id="to" type="date" v-model="toDate" />
    </div>
    <div class="home-buttons">
      <button class="btn btn-primary" @click="doReserve">Reserve</button>
    </div>
  </div>
</template>

<script>
import { reactive } from 'vue';
import { store } from '@/store';
import LernpartnerSelect from '@/components/LernpartnerSelect.vue';
import MaterialSelect from '@/components/MaterialSelect.vue';

export default {
  name: 'HomeView',
  data() {
    return {
      fromDate: null,
      toDate: null
    };
  },
  components: {
    LernpartnerSelect,
    MaterialSelect,
  },
  methods: {
    doReserve() {
      alert('Reserve');
      const payload = {
        fromDate: this.fromDate,
        toDate: this.toDate,
        lernpartner_id: store.lernpartner_id,
        equipment_id: store.equipment_id
      };

      fetch('https://projects.sbw.media/reservationview', {
        method: 'POST',
        headers: { 'Content-Type': 'application/json' },
        body: JSON.stringify(payload)
      })
        .then(response => response.json())
        .then(data => {
          console.log(data);
        })
        .catch(error => {
          console.error(error);
        });
    }
  }
};
</script>

<style scoped>
.form {
  width: 80%;
  display: grid;
  grid-template-columns: 0.4fr 0.5fr;
  gap: 1em;
}
</style>
