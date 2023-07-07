<template>
  <label for="material">Gerät</label>
  <select id="equipment" v-model="store.equipment_id">
    <option 
    v-for="item in equipment" 
    :value="equipment.ID">
      {{ item.Name }}
    </option>
  </select>
</template>
<script setup>
import {ref, watch} from 'vue';
import { store } from '@/store';
</script>
<script>
export default {
  name: "MaterialSelect",
  data() {
    return {
      equipment: []
    };
  },
  created() {
    this.getEquipment();
  },
  methods: {
    async getEquipment() {
      const response = await fetch("https://projects.sbw.media/equipment");
      this.equipment = await response.json();
      console.log(this.equipment);
    }
  }
};
</script>

<style></style>
