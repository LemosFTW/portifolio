<template>

  <div class="centerContainer">

    <HeaderComponent :fields="fields" :icons="icons" />


    <div class="gridHalf">

      <img src="@/assets/profile.jpg" alt="teste" class="imageProfile" loading="eager">

      <div class="descriptionContainer">
        <h1 class="name">{{ name }} {{ surname }}</h1>
        <DescriptionComponent :description="description" />
      </div>

    </div>
  </div>
</template>

<script>

import HeaderComponent from './components/HeaderComponent.vue'
import DescriptionComponent from './components/descriptionComponent.vue';

export default {
  name: 'App',
  components: {
    HeaderComponent,
    DescriptionComponent
  },
  data() {
    return {
      fields: [
        { title: 'About Me', description: '', externalContent: false },
        { title: 'Academic Life', description: '', externalContent: false },
        { title: 'Projects', description: '', externalContent: false },
        { title: 'Experience', description: '', externalContent: false }
      ],
      icons: [
        { title: '', imageUrl: require('@/assets/linkedinIcon.jpg'), externalContent: true },
        // { title: '', imageUrl: require('@/assets/githubIcon.jpg'), externalContent: true }
      ],
      name: 'Rodrigo',
      surname: 'Lemos Fernandes',
      description: 'I am a Software Engeneer, passionate about gain tech knowledge and improve my self.',
      academicLife: [
        { title: 'Bachelors in Computer Science and Engineering', University: 'New University of Lisbon, FCT', year: '2021 - 2024' },
        { title: 'Post Graduated in Cibersecurity', description: 'European University', year: '2024 - 2025' }
      ],
      projects: [
        { title: 'Project 1', description: 'Description 1', year: '2021', link: '' },
        { title: 'Project 2', description: 'Description 2', year: '2022', link: '' },
        { title: 'Project 3', description: 'Description 3', year: '2023', link: '' },
        { title: 'Project 4', description: 'Description 4', year: '2024', link: '' },
      ],
      experience: [
        { title: 'Software Engeneer', company: 'Company 1', year: '2022 - 2023' },
        { title: 'Software Engeneer', company: 'Company 2', year: '2022 - 2023' },
        { title: 'Software Engeneer', company: 'Company 3', year: '2023 - 2024' },
      ]
    }
  }
}




</script>

<style>
body {
  /* display: flex; */
  background-color: #080808;
  font-family: Arial, Helvetica, sans-serif;

}

.centerContainer {
  padding-right: 50px;
  padding-left: 50px;

}

.imageProfile {
  margin-top: 50px;
  width: 400px;
  height: 400px;
  border-radius: 50%;
  /* position: absolute;
  left: 55%;
  margin-top: 50px; */
  grid-column: 1;
}

.gridHalf {
  display: grid;
  grid-template-columns: 50% 50%;
  grid-column-start: 1;
  gap: 10px;
  align-items: center;

}

.descriptionContainer {
  grid-column: 2;
  overflow: visible;
}

.name {
  color: white;
}
</style>
