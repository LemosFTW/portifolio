<template>
  <div class="headerFixed">
    <HeaderComponent :fields="fields" :icons="icons" @section-click="handleSectionClick" />
  </div>
  <h1 class="title">{{ fields[0].title }}</h1>
  <div class="centerContainer">

    <div class="gridHalf">

      <img src="@/assets/profile.jpg" alt="teste" class="imageProfile" loading="eager">

      <div class="descriptionContainer">
        <h1 class="name">{{ name }} {{ surname }}</h1>
        <DescriptionComponent :description="description" />
      </div>



    </div>


    <h1 class="title">{{ fields[1].title }}</h1>
    <div class="gridHalf">
      <div class="academicLifeContainer">
        <div v-for="academic in academicLife" :key="academic.title">
          <div class="academicUniversity">
            <h3>{{ academic.title }}</h3>
            <p>{{ academic.university }} - {{ academic.year }}</p>

          </div>
        </div>
      </div>

      <div class="academicImageContainer">
        <img src="https://www.fct.unl.pt/sites/default/files/imagecache/l740/imagens/noticias/2021/02/campusfct.png"
          alt="Academic illustration" class="academicImage">
        <img src="https://forum.pt/images/IADE_1.jpg" alt="Academic illustration" class="academicImage">
      </div>

    </div>

    <h1 class="title">{{ fields[2].title }}</h1>
    <div class="gridHalf">
      <div>
        <div v-for="project in projects" :key="project.title">
          <div>
            <h3>{{ project.title }}</h3>
            <p>{{ project.description }}</p>
            <p>{{ project.year }}</p>
            <a v-if="project.link" :href="project.link">
              Ver projeto
            </a>
          </div>
        </div>
      </div>
    </div>

    <h1 class="title">{{ fields[3].title }}</h1>
    <div class="gridHalf">
      <div>
        <div v-for="exp in experience" :key="exp.title">
          <div>
            <h3>{{ exp.title }}</h3>
            <p>{{ exp.company }} - {{ exp.year }}</p>
          </div>
        </div>
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
        { title: 'Bachelors in Computer Science and Engineering', university: 'New University of Lisbon, FCT', year: '2021 - 2024' },
        { title: 'Post Graduated in Cibersecurity', university: 'European University', year: '2024 - 2025' }
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
  },
  methods: {
    handleSectionClick(title) {
      const titles = document.querySelectorAll('.title');
      const targetTitle = Array.from(titles).find(element =>
        element.textContent.trim().toLowerCase() === title.toLowerCase()
      );

      if (targetTitle) {
        targetTitle.scrollIntoView({ behavior: 'smooth' });
      }
    }
  }
}




</script>

<style>
body {
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
  grid-column: 1;
}

.gridHalf {
  display: grid;
  grid-template-columns: 50% 50%;
  grid-column-start: 1;
  gap: 10px;
}

.descriptionContainer {
  grid-column: 2;
  overflow: visible;
  align-self: center;

}

.name {
  color: white;
}

.academicLifeContainer {
  color: white;
  align-self: start;
  margin-top: 20px;

}

.academicLifeContainer p {
  margin-top: 0;
  margin-bottom: 20px;
  color: #cccccc;
}

.academicUniversity {
  padding-top: 25px;
}

.academicImage {
  max-width: 30%;
  height: auto;
  margin-left: 50%;
  margin-top: 30px;
  border-radius: 10px;
}

.title {
  color: white;
  text-align: center;
  margin-top: 50px;

}

.headerFixed {
  margin-right: 50px;
  margin-left: 50px;
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  z-index: 1000;
  background-color: #080808;

}

.centerContainer:first-of-type {
  padding-top: 80px;
}
</style>
