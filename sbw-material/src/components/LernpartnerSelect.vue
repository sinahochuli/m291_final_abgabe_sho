<template>

    <label for="lernpartner">Lernpartner</label>
    <select v-model="store.lernpartner_id">
      <option v-for="student in lernpartner" :value="student.ID" :key="student.ID">
        {{ student.Fullname }}
      </option>
    </select>
</template>

<script setup>
import { store } from '@/store';
</script>

<script>
export default {
  name: "LernpartnerSelect",
  data() {
    return {
      lernpartner: []
    };
  },
  created() {
    this.getLernpartner();
  },
  methods: {
    async getLernpartner() {
      
        const response = await fetch("https://projects.sbw.media/student");
        this.lernpartner = await response.json();
        console.log(this.lernpartner);
      
      }
    }
  };
</script>

<style></style>
