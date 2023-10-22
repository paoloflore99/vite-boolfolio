

<script>

import axios from 'axios';
export default {
  data() {
    return {
      projects: [],
    };
  },
  created() {
    this.fetchProjects();
  },
  methods: {
    fetchProjects() {
    
      axios.get('/api/projects')
        .then((response) => {
          
          this.projects = response.data;


          console.log(this.projects);
        })
        .catch((error) => {
          console.error('Errore durante la richiesta API:', error);
        });
    },
  },
};
</script>

<template>
  <div>
    <h1>Elenco dei Progetti</h1>
    <ul>
      <li v-for="project in projects" :key="project.id">
        {{ project.title }}
      </li>
    </ul>
  </div>
</template>


<style scoped>

</style>