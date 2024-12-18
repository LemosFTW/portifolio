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
        <DescriptionComponent :description="description" @icon-click="handleIconClick" />
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
          <div class="card" @click="handleClickProject(project.link)">
            <h3>{{ project.title }}</h3>
            <p>{{ project.description }}</p>
            <p><BsCalendar4Range class="calendar-icon" /> {{ project.year }}</p>
            <button v-if="project.link" 
                    @click="handleClickProject(project.link)" 
                    class="project-button">
              Ver projeto
            </button>
            <div class="techContainer">
              <div v-for="(Tech, index) in project.tech" :key="index" class="tech-icon">
                <component :is="Tech" />
              </div>
            </div>
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
            <p class="experience-date">
              <BsCalendar4Range class="calendar-icon" />
              {{ exp.company }} - {{ exp.year }}
            </p>
            <div v-for="description in exp.description" :key="description">
              <p><AkPointerRightFill class="pointer-icon" style="scale: 0.85;" /> {{ description }}</p>
            </div>
          
            <div class="techContainer">
              <div v-for="(Tech, index) in exp.tech" :key="index" class="tech-icon">
                <component :is="Tech" />
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>

  </div>
</template>

<script>

import HeaderComponent from './components/HeaderComponent.vue'
import DescriptionComponent from './components/descriptionComponent.vue';
import { DeLinkedinPlain,AkGithubFill,DeNodejsPlainWordmark ,DeVuejsOriginal, BsCalendar4Range, DeReactOriginal, DePostgresqlPlainWordmark, DeHtml5Original, DeCss3Original, DeJavascriptOriginal, DeTypescriptPlain, DePythonOriginalWordmark, DeJavaOriginal, DeDockerOriginal, DeGitOriginal, DeNextjsOriginalWordmark, DeNestjsOriginalWordmark, DeMongodbPlainWordmark } from '@kalimahapps/vue-icons';
import { AkPointerRightFill } from '@kalimahapps/vue-icons';
import { DeAmazonwebservicesPlainWordmark } from '@kalimahapps/vue-icons';
export default {
  
  name: 'App',
  components: {
    HeaderComponent,
    DescriptionComponent,
    DeAmazonwebservicesPlainWordmark,
    DeLinkedinPlain,
    AkPointerRightFill,
    AkGithubFill,
    DeNodejsPlainWordmark,
    BsCalendar4Range,
    DeReactOriginal,
    DePostgresqlPlainWordmark,
    DeHtml5Original,
    DeCss3Original,
    DeJavascriptOriginal,
    DeTypescriptPlain,
    DePythonOriginalWordmark,
    DeJavaOriginal,
    DeDockerOriginal,
    DeGitOriginal,
    DeNextjsOriginalWordmark,
    DeNestjsOriginalWordmark,
    DeMongodbPlainWordmark,
    DeVuejsOriginal
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
        { title: 'Linkedin', imageUrl: DeLinkedinPlain, url: 'https://www.linkedin.com/in/rodrigolemosdev/' },
        { title: 'Github', imageUrl: AkGithubFill, url: 'https://github.com/LemosFTW' },
      ],
      name: 'Rodrigo',
      surname: 'Lemos Fernandes',
      description: 'I am a Software Engeneer, passionate about gain tech knowledge and improve my self.',
      academicLife: [
        { title: 'Bachelors in Computer Science and Engineering', university: 'New University of Lisbon, FCT', year: '2021 - 2024' },
        { title: 'Post Graduated in Cibersecurity', university: 'European University', year: '2024 - 2025' }
      ],
      projects: [
        { title: 'Invoice Reader', description: 'This project is a tool that allows you to upload invoices, and extract the data from them, saving it in a postgres database.', year: '2021', link: 'https://github.com/LemosFTW/Backend-InvoiceReader', tech: [DePostgresqlPlainWordmark, DeJavascriptOriginal, DeTypescriptPlain, DeReactOriginal, DeNextjsOriginalWordmark, DeNestjsOriginalWordmark, DeGitOriginal]},
        { title: 'FreeCol Game Extension', description: 'This was a project from a subject at university, where we had to create 3 new features from an open source game.', year: '2022', link: 'https://github.com/LemosFTW/Freecol-New-Features' , tech: [DeJavaOriginal, DeGitOriginal]},
        { title: 'Image Reader', description: 'This project is a tool that reads images and extract the content from them.', year: '2023', link: 'https://github.com/LemosFTW/NextJs_Read_Image_Content', tech: [DeReactOriginal, DeNextjsOriginalWordmark, DeTypescriptPlain, DeCss3Original, DeHtml5Original, DeGitOriginal]},
        { title: 'Portifolio (Source Code from this WebPage)', description: 'Portifolio page.', year: '2024', link: 'https://github.com/LemosFTW/Portifolio' , tech: [DeVuejsOriginal, DeGitOriginal]},
      ],
      experience: [
        { title: 'FrontEnd Developer - Volunteer', company: 'Ocas GNO', year: '2023', description: ['Worked for OCAS ONG, building their Website.','Leader of the development team to build the website.'] , tech: [DeHtml5Original, DeCss3Original, DeJavascriptOriginal, DeGitOriginal] },
        { title: 'FullStack Software Engeneer - Internship', company: 'Clearis S.A.', year: '2024',description: ["I've worked for Clearis, developing an application to manage product demand, product delivery by suppliers, and contract management.",'The main client was Galp and their subsidiaries all around the world.','The main project I developed was a client and supplier chat, wherein suppliers communicate with Galp to resolve pending issues.'] , tech: [DeReactOriginal, DeVuejsOriginal, DeTypescriptPlain, DeCss3Original, DeMongodbPlainWordmark,DeGitOriginal] },
        { title: 'Backend Software Engeneer', company: 'DUOP', year: '2024', description: ["Worked for DUOP, building a whatsapp chatbot using Python and AI Agents to answer the clients.","To build the AI Agents, I had to set all the Knowledge Bases using Pinecone (Vector Database) and to automate the process I had to create some lambdas functions in AWS."] ,   tech: [DePythonOriginalWordmark, DePostgresqlPlainWordmark, DeJavascriptOriginal,DeAmazonwebservicesPlainWordmark, DeGitOriginal] },
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
    },
    handleClickProject(link) {
      if (link) {
        window.open(link, '_blank');
      }
    },
    handleIconClick(url) {
      if (url) {
        window.open(url, '_blank');
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
.card:hover {
  background-color: #2B2B2B;
}

.experience-date {
  display: flex;
  align-items: center;
  gap: 8px;
}

.calendar-icon {
  width: 16px;
  height: 16px;
  color: #cccccc;
}

.techContainer {
  display: flex;
  flex-wrap: wrap;
  gap: 12px;
  margin-top: 15px;
}

.tech-icon {
  width: 30px;
  height: 30px;
  display: flex;
  align-items: center;
  justify-content: center;
}

.tech-icon svg {
  width: 100%;
  height: 100%;
  transition: transform 0.2s ease;
}

.tech-icon:hover svg {
  transform: scale(1.2);
}

.project-button {
  margin-bottom: 1rem;
  background-color: #42b983;
  color: white;
  border: none;
  padding: 8px 16px;
  border-radius: 4px;
  cursor: pointer;
  font-size: 14px;
  margin-top: 12px;
  transition: background-color 0.2s ease;
}

.project-button:hover {
  background-color: #3aa876;
}




</style>
