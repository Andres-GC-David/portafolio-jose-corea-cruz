<template>
  <section class="projects-section">
    <div class="container">

      <h2 class="section-title">Proyectos</h2>

      <!-- Filter dropdown -->
      <div class="filter-bar">
        <label for="tag-filter">Filtrar por etiqueta:</label>
            <div class="custom-select-wrapper">
                <select id="tag-filter" v-model="selectedTag" class="custom-select">
                <option value="">— Todos —</option>
                <option v-for="tag in tags" :key="tag" :value="tag">
                    {{ tag }}
                </option>
                </select>
            </div>
        </div>

      <!-- Carousel wrapper -->
      <div class="carousel-wrapper">
        <button class="nav-button prev" @click="scroll(-1)">‹</button>
        <div class="carousel" ref="carousel">
          <div
            v-for="(p, idx) in filteredProjects"
            :key="idx"
            class="project-card"
          >
            <img :src="p.image" :alt="p.name" class="project-image" />
            <div class="project-details">
              <h3>{{ p.name }}</h3>
              <p>{{ p.description }}</p>
              <p><strong>Cliente:</strong> {{ p.client }}</p>
              <div class="tags">
                <span v-for="t in p.tags" :key="t" class="tag">{{ t }}</span>
              </div>
              <a :href="p.pdf" target="_blank" class="view-button">
                Ver PDF
              </a>
            </div>
          </div>
          <div v-if="!filteredProjects.length" class="no-results">
            No hay proyectos para “{{ selectedTag }}”
          </div>
        </div>
        <button class="nav-button next" @click="scroll(1)">›</button>
      </div>

    </div>
  </section>
</template>

<script>
import projectsData from "../data/projects.json";

export default {
  name: "Projects",
  data() {
    return {
      allProjects: projectsData,
      selectedTag: "",
    };
  },
  computed: {
    tags() {
      // unique sorted tags
      const set = new Set();
      this.allProjects.forEach((p) => p.tags.forEach((t) => set.add(t)));
      return Array.from(set).sort();
    },
    filteredProjects() {
      if (!this.selectedTag) return this.allProjects;
      return this.allProjects.filter((p) =>
        p.tags.includes(this.selectedTag)
      );
    },
  },
  methods: {
    scroll(direction) {
      const container = this.$refs.carousel;
      // card width + gap = ~ 350px (adjust if you change CSS)
      const scrollAmount = direction * 350;
      container.scrollBy({ left: scrollAmount, behavior: "smooth" });
    },
  },
};
</script>

<style scoped>
.projects-section {
  padding: 5rem 1rem;
  background: linear-gradient(to right, #f5f7fa, #e5edf3);
}
.section-title {
  text-align: center;
  font-size: 2.5rem;
  margin-bottom: 2rem;
  color: #2c3e50;
}
.filter-bar {
  display: flex;
  flex-direction: column;
  align-items: center;
  background: #ffffff;
  border-radius: 16px;
  box-shadow: 0 10px 30px rgba(0, 0, 0, 0.05);
  padding: 2rem 1rem;
  margin: 2rem auto;
  max-width: 600px;
  transition: all 0.3s ease-in-out;
}

.filter-bar h4 {
  font-size: 1.3rem;
  color: #2c3e50;
  margin-bottom: 1rem;
  text-align: center;
}

.filter-bar select {
  padding: 0.5rem 1rem;
  font-size: 1rem;
  border-radius: 8px;
  border: 1px solid #ccc;
  transition: border-color 0.3s;
}
.filter-bar select:focus {
  border-color: #4ca1af;
}

.carousel-wrapper {
  position: relative;
  display: flex;
  align-items: center;
  overflow: hidden;
  padding: 2rem 1rem;
}
/*** */

.carousel-wrapper::before,
.carousel-wrapper::after {
  content: "";
  position: absolute;
  top: 0;
  width: 60px;
  height: 100%;
  z-index: 1;
  pointer-events: none;
  transition: opacity 0.3s ease;
}
.carousel-wrapper::before {
  left: 0;
  background: linear-gradient(to right, rgba(250, 250, 250, 1), rgba(250, 250, 250, 0));
}
.carousel-wrapper::after {
  right: 0;
  background: linear-gradient(to left, rgba(250, 250, 250, 1), rgba(250, 250, 250, 0));
}
.carousel-wrapper:hover::before,
.carousel-wrapper:hover::after {
  opacity: 1;
}

/*** */

.carousel {
  width: 100%;
  display: flex;
  overflow-x: auto;
  scroll-behavior: smooth;
  gap: 1.5rem;
  padding: 1rem 0;
  scroll-padding: 1rem;
}
.carousel::-webkit-scrollbar {
  display: none;
}

.project-card {
  flex: 0 0 320px;
  background: white;
  border-radius: 12px;
  box-shadow: 0 10px 30px rgba(0, 0, 0, 0.08);
  transition: transform 0.3s, box-shadow 0.3s;
}
.project-card:hover {
  transform: translateY(-8px);
  box-shadow: 0 20px 40px rgba(0, 0, 0, 0.12);
}

.project-image {
  width: 100%;
  border-top-left-radius: 12px;
  border-top-right-radius: 12px;
}
.project-details {
  padding: 1rem;
}
.project-details h3 {
  margin: 0 0 0.5rem;
  color: #2c3e50;
}
.project-details p {
  margin: 0.3rem 0;
  color: #555;
  font-size: 0.95rem;
}
.tags {
  margin: 0.5rem 0;
}
.tag {
  display: inline-block;
  background: #4ca1af;
  color: white;
  padding: 0.2rem 0.6rem;
  border-radius: 4px;
  font-size: 0.8rem;
  margin-right: 0.3rem;
}

.view-button {
  display: block;
  text-align: center;
  margin-top: 0.8rem;
  padding: 0.5rem 1rem;
  background: #2c3e50;
  color: white;
  border-radius: 6px;
  text-decoration: none;
  transition: background 0.3s;
}
.view-button:hover {
  background: #4ca1af;
}

.nav-button {
  background: none;
  border: none;
  font-size: 2rem;
  color: #2c3e50;
  cursor: pointer;
  padding: 0 0.5rem;
  transition: color 0.3s, transform 0.2s;
}
.nav-button:hover {
  color: #4ca1af;
  transform: scale(1.2);
}

.no-results {
  font-size: 1.1rem;
  color: #888;
  padding: 2rem;
}

/**** */

/* Modern dropdown style */
.custom-select-wrapper {
  position: relative;
  width: 100%;
}
.custom-select {
  width: 100%;
  appearance: none;
  background-color: white;
  border: 1px solid #ccc;
  border-radius: 12px;
  padding: 0.75rem 2.5rem 0.75rem 1rem;
  font-size: 1rem;
  color: #2c3e50;
  cursor: pointer;
  transition: all 0.3s ease;
  background-image: url('data:image/svg+xml;utf8,<svg fill="%234ca1af" height="18" viewBox="0 0 24 24" width="18" xmlns="http://www.w3.org/2000/svg"><path d="M7 10l5 5 5-5z"/></svg>');
  background-repeat: no-repeat;
  background-position: right 1rem center;
  background-size: 1rem;
}
.custom-select:focus {
  outline: none;
  border-color: #4ca1af;
  box-shadow: 0 0 0 4px rgba(76, 161, 175, 0.2);
}


@media (max-width: 768px) {
  .carousel {
    gap: 1rem;
  }

  .project-card {
    flex: 0 0 85%;
  }

  .carousel-wrapper::before,
  .carousel-wrapper::after {
    width: 30px;
  }
}

@media (max-width: 480px) {
  .project-card {
    flex: 0 0 95%;
  }

  .carousel-wrapper {
    padding: 1rem 0.5rem;
  }
}

</style>
