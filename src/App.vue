<template>
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
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
      <div class="projectsContainer">
        <div v-for="project in projects" :key="project.title">
          <div class="card">
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
      <div class="experienceContainer">
        <div v-for="exp in experience" :key="exp.title">
          <div class="card">
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
        { title: 'Invoice Reader', description: 'This project is a tool that allows you to upload invoices, and extract the data from them, saving it in a postgres database.', year: '2021', link: '' },
        { title: 'FreeCol Game Extension', description: 'This was a project from a subject at university, where we had to create 3 new features from an open source game.', year: '2022', link: 'https://github.com/LemosFTW/Freecol-New-Features' },
        { title: 'Image Reader', description: 'This project is a tool that reads images and extract the content from them.', year: '2023', link: 'https://github.com/LemosFTW/NextJs_Read_Image_Content' },
        { title: 'Portifolio (Source Code from this WebPage)', description: 'Portifolio page.', year: '2024', link: 'https://github.com/LemosFTW/Portifolio' },
      ],
      experience: [
        { title: 'FrontEnd Developer - Volunteer', company: 'Ocas GNO', year: '2023' },
        { title: 'FullStack Software Engeneer - Internship', company: 'Clearis S.A.', year: '2024' },
        { title: 'Backend Software Engeneer', company: 'DUOP', year: '2024' },
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
  grid-template-columns: 1fr 1fr;
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

.projectsContainer {
  grid-column: 1/-1;
  display: flex;
  flex-direction: column;
  gap: 20px;
}

.projectsContainer h3 {
  margin-bottom: 2rem;
  color: white;
}

.projectsContainer p {
  margin-top: 0;
  color: #cccccc;
}

.projectsContainer p:first-of-type {
  grid-column: 2;
}

.experienceContainer {
  grid-column: 1/-1;
  display: flex;
  flex-direction: column;
  gap: 20px;
} 

.experienceContainer h3 {
  margin-bottom: 0;
  color: white;
}

.experienceContainer p {
  margin-top: 0;
  color: #cccccc;
}

@media screen and (max-width: 768px) {
  .centerContainer {
    padding-right: 20px;
    padding-left: 20px;
  }

  .gridHalf {
    grid-template-columns: 1fr; /* Muda para uma coluna única */
    gap: 20px;
  }

  .imageProfile {
    width: 300px;
    height: 300px;
    margin: 30px auto;
    display: block;
  }

  .descriptionContainer {
    grid-column: 1;
    text-align: center;
    margin-top: 20px;
  }

  .academicImage {
    margin-left: 0;
    max-width: 80%;
    display: block;
    margin: 20px auto;
  }
}

@media screen and (max-width: 480px) {
  .imageProfile {
    width: 250px;
    height: 250px;
  }

  .centerContainer {
    padding-right: 15px;
    padding-left: 15px;
  }

  .name {
    font-size: 1.5rem;
  }

  .academicImage {
    max-width: 100%;
  }

  .headerFixed {
    margin-right: 15px;
    margin-left: 15px;
  }
}

.container {
  width: 80%;
  margin: 0 auto;
  max-width: 1200px;
}

.content {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
  gap: 20px;
}

.flex-container {
  display: flex;
  flex-wrap: wrap;
  gap: 20px;
}

.flex-item {
  flex: 1;
  min-width: 300px;
}

.card {
  background-color: #1B1B1B;
  border-radius: 10px;
  padding: 20px;
  grid-template-columns: 1fr;
  /* grid-column-start: 1; */
  /* grid-column-end: span 2; */
  
  
}

</style>
