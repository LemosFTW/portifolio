<template>
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <div class="headerFixed">
    <HeaderComponent
      :fields="fields"
      :icons="icons"
      @section-click="handleSectionClick"
      @icon-click="handleIconClick"
    />
  </div>
  <h1 class="title animate-on-scroll">{{ fields[0].title }}</h1>
  <div class="centerContainer">
    <div class="gridHalf">
      <img
        src="@/assets/profile.jpg"
        alt="teste"
        class="imageProfile animate-on-scroll"
        loading="eager"
      />

      <div class="descriptionContainer animate-on-scroll" style="transition-delay: 0.15s">
        <h1 class="name">{{ name }} {{ surname }}</h1>
        <DescriptionComponent :description="description" />
      </div>
    </div>

    <h1 class="title animate-on-scroll">{{ fields[1].title }}</h1>
    <div class="academicLifeContainer">
      <div
        v-for="(academic, index) in academicLife"
        :key="academic.title"
        class="academicItem animate-on-scroll"
        :style="{ transitionDelay: index * 0.12 + 's' }"
      >
        <div class="academicUniversity">
          <h3>{{ academic.title }}</h3>
          <p>{{ academic.university }} - {{ academic.year }}</p>
        </div>
        <img
          :src="academicImages[index]"
          :alt="academic.university"
          class="academicImage"
        />
      </div>
    </div>

    <h1 class="title animate-on-scroll">{{ fields[2].title }}</h1>
    <div class="gridHalf">
      <div class="projectsContainer">
        <div
          v-for="(project, index) in projects"
          :key="project.title"
          class="animate-on-scroll"
          :style="{ transitionDelay: index * 0.1 + 's' }"
        >
          <div class="card" @click="handleClickProject(project.link)">
            <h3>{{ project.title }}</h3>
            <p>{{ project.description }}</p>
            <p><BsCalendar4Range class="calendar-icon" /> {{ project.year }}</p>
            <button
              v-if="project.link"
              @click.stop="handleClickProject(project.link)"
              class="project-button"
            >
              Go to Project
            </button>
            <div class="techContainer">
              <div
                v-for="(Tech, techIndex) in project.tech"
                :key="techIndex"
                class="tech-icon"
              >
                <component :is="Tech" />
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>

    <h1 class="title animate-on-scroll">{{ fields[3].title }}</h1>
    <div class="gridHalf">
      <div class="experienceContainer">
        <div
          v-for="(exp, index) in experience"
          :key="exp.title"
          class="animate-on-scroll"
          :style="{ transitionDelay: index * 0.1 + 's' }"
        >
          <div class="card">
            <h3>{{ exp.title }}</h3>
            <p class="experience-date">
              <BsCalendar4Range class="calendar-icon" />
              {{ exp.company }} - {{ exp.year }}
            </p>
            <div v-for="description in exp.description" :key="description">
              <p>
                <AkPointerRightFill class="pointer-icon" style="scale: 0.85" />
                {{ description }}
              </p>
            </div>

            <div class="techContainer">
              <div
                v-for="(Tech, techIndex) in exp.tech"
                :key="techIndex"
                class="tech-icon"
              >
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
import HeaderComponent from "./components/HeaderComponent.vue";
import DescriptionComponent from "./components/descriptionComponent.vue";
import {
  DeLinkedinPlain,
  BxGmail,
  AkPointerRightFill,
  DeAmazonwebservicesPlainWordmark,
  AkGithubFill,
  DeNodejsPlainWordmark,
  DeVuejsOriginal,
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
} from "@kalimahapps/vue-icons";

export default {
  name: "App",
  components: {
    HeaderComponent,
    DescriptionComponent,
    BxGmail,
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
    DeVuejsOriginal,
  },
  data() {
    return {
      fields: [
        { title: "About Me", description: "", externalContent: false },
        { title: "Academic Life", description: "", externalContent: false },
        { title: "Projects", description: "", externalContent: false },
        { title: "Experience", description: "", externalContent: false },
      ],
      icons: [
        {
          title: "Linkedin",
          imageUrl: DeLinkedinPlain,
          url: "https://www.linkedin.com/in/rodrigolemosdev/",
        },
        {
          title: "Github",
          imageUrl: AkGithubFill,
          url: "https://github.com/LemosFTW",
        },
        {
          title: "Gmail",
          imageUrl: BxGmail,
          url: "mailto:rlemos584@gmail.com",
        },
      ],
      name: "Rodrigo",
      surname: "Lemos Fernandes",
      description:
        "Full Stack Software Engineer with 3 years of professional experience across the entire software development lifecycle. Strong expertise in Back-End development using Node.js, Java, and Python to design and maintain scalable RESTful APIs, as well as Front-End development using Vue 3 and React to build high-quality, user-centric web applications.",
      academicImages: [
        "https://external-content.duckduckgo.com/iu/?u=https%3A%2F%2Fwww.puc-rio.br%2Fsobrepuc%2Fcampus%2Fimagens%2Fimg_campus_banner_index.jpg",
        "https://forum.pt/images/IADE_1.jpg",
        "https://www.fct.unl.pt/sites/default/files/imagecache/l740/imagens/noticias/2021/02/campusfct.png",
      ],
      academicLife: [
        {
          title: "Master's Degree in Computer Science",
          university: "Pontifical Catholic University of Rio de Janeiro",
          year: "2025 - Present",
        },
        {
          title: "Postgraduate Degree in Cybersecurity",
          university: "European University",
          year: "2024 - 2025",
        },
        {
          title:
            "Bachelor's Degree in Computer Engineering and Computer Science",
          university: "NOVA University of Lisbon",
          year: "2021 - 2024",
        },
      ],
      projects: [
        {
          title: "Factored Project",
          description:
            "A Next.js web application with Films and Characters pages, built with TypeScript and Tailwind CSS. Deployed on Vercel with Docker support.",
          year: "2025",
          link: "https://github.com/LemosFTW/FactoredProject",
          tech: [
            DeTypescriptPlain,
            DeReactOriginal,
            DeNextjsOriginalWordmark,
            DeDockerOriginal,
            DeGitOriginal,
          ],
        },
        {
          title: "Invoice Reader",
          description:
            "This project is a tool that allows you to upload invoices and other documents, and extract the data from them, saving it in a postgres database and S3.",
          year: "2025",
          link: "https://github.com/LemosFTW/PaggoProject",
          tech: [
            DePostgresqlPlainWordmark,
            DeJavascriptOriginal,
            DeTypescriptPlain,
            DeReactOriginal,
            DeNextjsOriginalWordmark,
            DeNestjsOriginalWordmark,
            DeGitOriginal,
            DeDockerOriginal,
            DeAmazonwebservicesPlainWordmark,
          ],
        },
        {
          title: "FreeCol Game Extension",
          description:
            "This was a project from a subject at university, where we had to create 3 new features from an open source game.",
          year: "2023",
          link: "https://github.com/LemosFTW/Freecol-New-Features",
          tech: [DeJavaOriginal, DeGitOriginal],
        },
        {
          title: "Portifolio (Source Code from this WebPage)",
          description: "Portifolio page.",
          year: "2024",
          link: "https://github.com/LemosFTW/Portifolio",
          tech: [DeVuejsOriginal, DeGitOriginal],
        },
      ],
      experience: [
        {
          title: "Software Engineer",
          company: "ExACTa",
          year: "Aug 2025 - Present",
          description: [
            "Worked as a Full Stack Engineer developing and maintaining scalable web applications using React with Redux on the front end and Python with FastAPI on the back end.",
            "Designed, extended, and maintained RESTful APIs, ensuring reliable communication between front-end applications and back-end services.",
            "Collaborated closely with engineering and product teams to improve application performance, reliability, and user experience.",
            "Contributed to code reviews, testing strategies, and version control best practices, ensuring high-quality and maintainable codebases.",
          ],
          tech: [
            DeReactOriginal,
            DePythonOriginalWordmark,
            DeGitOriginal,
            DeDockerOriginal,
          ],
          link: "",
        },
        {
          title: "Software Engineer",
          company: "DUOP",
          year: "Jun 2024 - Aug 2025",
          description: [
            "Developed Back-End services using Node.js, Python (Django), and CrewAI, focusing on API design, data processing, and system scalability.",
            "Led a small engineering team in the development of an AI-powered chatbot for investment-related inquiries, integrating Large Language Models (LLMs) and Retrieval-Augmented Generation (RAG) techniques.",
            "Designed and deployed CI/CD pipelines using GitHub Actions, Docker, and AWS, reducing deployment time and accelerating release cycles by approximately 80%.",
            "Worked with relational (SQL) and vector databases (Pinecone) to support data retrieval, indexing, and analytical workflows.",
          ],
          tech: [
            DePythonOriginalWordmark,
            DeNodejsPlainWordmark,
            DePostgresqlPlainWordmark,
            DeAmazonwebservicesPlainWordmark,
            DeGitOriginal,
            DeDockerOriginal,
          ],
          link: "",
        },
        {
          title: "Full Stack Software Engineering Intern",
          company: "Clearis S.A.",
          year: "Dec 2023 - Jun 2024",
          description: [
            "Developed a web-based application for product demand management, supplier deliveries, and contract administration.",
            "Designed and implemented a sub-module that optimized nearly 90% of the communication flow between a major client and over 10,000 global suppliers.",
            "Delivered scalable and maintainable solutions using JavaScript, TypeScript, Vue 3, React, MongoDB, and Node.js.",
            "Worked within an existing codebase, contributing new features while maintaining system stability and performance.",
          ],
          tech: [
            DeReactOriginal,
            DeVuejsOriginal,
            DeTypescriptPlain,
            DeCss3Original,
            DeMongodbPlainWordmark,
            DeGitOriginal,
          ],
          link: "",
        },
        {
          title: "FrontEnd Developer - Volunteer",
          company: "Ocas ONG",
          year: "2023",
          description: [
            "Worked for OCAS ONG, building their Website.",
            "Leader of the development team to build the website.",
          ],
          tech: [
            DeHtml5Original,
            DeCss3Original,
            DeJavascriptOriginal,
            DeGitOriginal,
          ],
          link: "",
        },
      ],
    };
  },
  mounted() {
    this.observer = new IntersectionObserver(
      (entries) => {
        entries.forEach((entry) => {
          if (entry.isIntersecting) {
            entry.target.classList.add("visible");
          }
        });
      },
      { threshold: 0.1 }
    );

    this.$nextTick(() => {
      document.querySelectorAll(".animate-on-scroll").forEach((el) => {
        this.observer.observe(el);
      });
    });
  },
  beforeUnmount() {
    if (this.observer) {
      this.observer.disconnect();
    }
  },
  methods: {
    handleSectionClick(title) {
      const titles = document.querySelectorAll(".title");
      const targetTitle = Array.from(titles).find(
        (element) =>
          element.textContent.trim().toLowerCase() === title.toLowerCase(),
      );

      if (targetTitle) {
        targetTitle.scrollIntoView({ behavior: "smooth" });
      }
    },
    handleClickProject(link) {
      if (link) {
        window.open(link, "_blank");
      }
    },
    handleIconClick(url) {
      if (!url) return;

      if (url.startsWith("mailto:")) {
        window.location.href = url;
      } else {
        window.open(url, "_blank");
      }
    },
  },
};
</script>

<style>
body {
  background-color: #080808;
  font-family: Arial, Helvetica, sans-serif;
}

.animate-on-scroll {
  opacity: 0;
  transform: translateY(30px);
  transition: opacity 0.6s ease, transform 0.6s ease;
}

.animate-on-scroll.visible {
  opacity: 1;
  transform: translateY(0);
}

.title {
  color: white;
  text-align: center;
  margin-top: 50px;
  position: relative;
  display: inline-block;
  left: 50%;
  transform: translateX(-50%) translateY(30px);
}

.title.visible {
  transform: translateX(-50%) translateY(0);
}

.title::after {
  content: "";
  position: absolute;
  bottom: -6px;
  left: 50%;
  width: 50px;
  height: 3px;
  background-color: #42b983;
  border-radius: 2px;
  transform: translateX(-50%) scaleX(0);
  transition: transform 0.5s ease 0.3s;
  transform-origin: center;
}

.title.visible::after {
  transform: translateX(-50%) scaleX(1);
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
  transition: opacity 0.6s ease, transform 0.6s ease, box-shadow 0.4s ease;
}

.imageProfile.visible:hover {
  box-shadow: 0 0 30px rgba(66, 185, 131, 0.25);
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
  grid-column: 1/-1;
  color: white;
  margin-top: 20px;
  display: flex;
  flex-direction: column;
  gap: 0;
}

.academicItem {
  display: flex;
  align-items: center;
  gap: 30px;
  padding: 20px 0;
  border-bottom: 1px solid #2b2b2b;
}

.academicItem:last-child {
  border-bottom: none;
}

.academicUniversity {
  flex: 1;
}

.academicLifeContainer p {
  margin-top: 4px;
  margin-bottom: 0;
  color: #cccccc;
}

.academicImage {
  width: 160px;
  height: 105px;
  object-fit: cover;
  border-radius: 10px;
  flex-shrink: 0;
  transition: opacity 0.6s ease, transform 0.6s ease;
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

.card {
  background-color: #1b1b1b;
  border-radius: 10px;
  padding: 20px;
  grid-template-columns: 1fr;
  transition: background-color 0.3s ease, transform 0.3s ease,
    box-shadow 0.3s ease;
}

.card:hover {
  background-color: #2b2b2b;
  transform: translateY(-4px);
  box-shadow: 0 8px 24px rgba(66, 185, 131, 0.12);
  cursor: pointer;
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
  transition: background-color 0.2s ease, transform 0.2s ease;
}

.project-button:hover {
  background-color: #3aa876;
  transform: scale(1.04);
}

@media screen and (max-width: 768px) {
  .centerContainer {
    padding-right: 20px;
    padding-left: 20px;
  }

  .gridHalf {
    grid-template-columns: 1fr;
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

  .academicItem {
    flex-direction: column;
    align-items: flex-start;
    gap: 16px;
  }

  .academicImage {
    width: 100%;
    height: 180px;
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
    height: 140px;
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
</style>
