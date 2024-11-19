<template>

  <div class="centerContainer">

    <HeaderComponent :fields="fields" :icons="icons" />

    <DescriptionComponent :description="description"/>
    <img src="assets/profile.jpg" alt="teste"  loading="eager"> 
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
        { title: 'Projects', description: '' , externalContent: false},
        { title: 'Experience', description: '',externalContent: false }
      ],
      icons : [
      { title: '', imageUrl: '../assets/linkedinIcon.jpg', externalContent: true },
      { title: '', imageUrl: '../assets/githubIcon.jpg', externalContent: true }
      ],
      imageProfile: '../assets/profile.jpg',
      name: 'Rodrigo',
      surname: 'Fernandes',
      description: 'I am a Software Engeneer, passionate about gain tech knowledge and improve my self.',
      academicLife: [
        { title: 'Bachelors in Computer Science and Engineering', University: 'New University of Lisbon, FCT', year: '2021 - 2024' },
        { title: 'Post Graduated in Cibersecurity', description: 'European University', year: '2024 - 2025' }
      ],
      projects: [
        { title: 'Project 1', description: 'Description 1', year: '2021', link: ''},
        { title: 'Project 2', description: 'Description 2', year: '2022', link: ''},
        { title: 'Project 3', description: 'Description 3', year: '2023', link: ''},
        { title: 'Project 4', description: 'Description 4', year: '2024', link: ''},
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

.centerContainer{
padding-right: 50px;
padding-left: 50px;

}
</style>
