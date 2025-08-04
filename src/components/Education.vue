<template>
  <section class="education-section">
    <div class="container">
      <h2 class="section-title">Formación Académica</h2>
      <div class="education-grid">
        <div class="education-card" :style="{ animationDelay: `0s` }">
          <div class="icon-box">
            <i class="fas fa-graduation-cap"></i>
          </div>
          <div class="education-info">
            <h3>Bachillerato y Licenciatura en Arquitectura</h3>
            <p class="institution">Universidad Latina de Costa Rica</p>
            <p class="date">2022 - Presente</p>
            <p class="description">
              Actualmente cursando el programa de Bachillerato en Arquitectura, con enfoque en diseño,
              procesos creativos y comprensión del entorno urbano.
            </p>
          </div>
        </div>
      </div>

      <h2 class="section-title" style="margin-top: 5rem;">Habilidades</h2>
      <div class="skills-grid">
        <div class="skills-card">
          <h3><i class="fas fa-tools"></i> Habilidades Técnicas</h3>
          <div class="skills-list">
            <div class="skill-item" v-for="(skill, index) in technicalSkills" :key="'tech-' + index">
              <img :src="`/src/assets/icons/${skill}`" alt="Icono" class="skill-icon" />
              <span>{{ skill.name }}</span>
            </div>
          </div>
        </div>
        <div class="skills-card">
          <h3><i class="fas fa-user-friends"></i> Habilidades Blandas</h3>
          <div class="skills-list">
            <div class="skill-item" v-for="(skill, index) in softSkills" :key="'soft-' + index">
              <img :src="`/src/assets/icons/${skill}`" alt="Icono" class="skill-icon" />
              <span>{{ skill.name }}</span>
            </div>
          </div>
        </div>
      </div>

    </div>
  </section>
</template>

<script>
export default {
  name: "EducationAndSkills",
  data() {
    return {
      technicalSkills: [
        { name: "Revit ARQ", icon: "revit-ARQ-icon.png" },
        { name: "Revit MEP", icon: "revit-ARQ-icon.png" },
        { name: "Revit STR", icon: "revit-ARQ-icon.png" },
        { name: "Excel", icon: "excel-icon.png" },
        { name: "Procore", icon: "procore-icon.png" },
      ],
      softSkills: [
        { name: "Comunicación efectiva con clientes", icon: "cliente.png" },
        { name: "Gestión del tiempo y entrega", icon: "tiempo.png" },
        { name: "Trabajo en equipo multidisciplinario", icon: "trabajo.png" },
        { name: "Capacidad de adaptación", icon: "adaptacion.png" },
        { name: "Pensamiento crítico y creativo", icon: "pensamiento.png" },
        { name: "Resolución de problemas", icon: "problema.png" },
      ],
    };
  },
};
</script>

<style scoped>
.education-section {
  background: linear-gradient(to right, #f5f7fa, #e5edf3);
  padding: 5rem 1rem;
}
.container {
  max-width: 1200px;
  margin: 0 auto;
}
.section-title {
  text-align: center;
  font-size: 2.7rem;
  color: #2c3e50;
  margin-bottom: 3rem;
}

/* Education Card */
.education-grid {
  display: flex;
  justify-content: center;
}
.education-card {
  background: white;
  padding: 2rem;
  border-radius: 16px;
  box-shadow: 0 12px 24px rgba(0, 0, 0, 0.08);
  display: flex;
  gap: 1.2rem;
  transition: transform 0.3s ease, box-shadow 0.3s ease;
  animation: fadeInUp 0.6s ease forwards;
  opacity: 0;
  transform: translateY(30px);
}
.education-card:hover {
  transform: translateY(-10px);
  box-shadow: 0 20px 40px rgba(0, 0, 0, 0.12);
}
.icon-box {
  font-size: 2.5rem;
  color: #4ca1af;
}
.education-info h3 {
  font-size: 1.5rem;
  color: #2c3e50;
  margin: 0;
}
.institution {
  font-weight: bold;
  color: #7f8c8d;
}
.date {
  font-size: 0.9rem;
  color: #95a5a6;
  margin-bottom: 0.5rem;
}
.description {
  font-size: 1rem;
  color: #444;
  line-height: 1.5;
}

/* Skills */
.skills-grid {
  display: flex;
  flex-wrap: wrap;
  gap: 2rem;
  justify-content: center;
  margin-top: 2rem;
}
.skills-card {
  flex: 1 1 300px;
  background: white;
  padding: 2rem;
  border-radius: 16px;
  box-shadow: 0 12px 24px rgba(0, 0, 0, 0.08);
  transition: transform 0.3s ease, box-shadow 0.3s ease;
}
.skills-card:hover {
  transform: translateY(-10px);
  box-shadow: 0 20px 40px rgba(0, 0, 0, 0.12);
}
.skills-card h3 {
  font-size: 1.3rem;
  color: #34495e;
  margin-bottom: 1rem;
}
.skills-card ul {
  list-style: none;
  padding: 0;
}
.skills-card li {
  padding: 0.3rem 0;
  font-size: 1rem;
  color: #555;
}

/* Animation */
@keyframes fadeInUp {
  to {
    opacity: 1;
    transform: translateY(0);
  }
}

.skills-list {
  display: flex;
  flex-wrap: wrap;
  gap: 1rem;
  justify-content: flex-start;
  margin-top: 1rem;
}

.skill-item {
  display: flex;
  align-items: center;
  gap: 0.7rem;
  background: #f7f9fb;
  padding: 0.7rem 1rem;
  border-radius: 12px;
  box-shadow: 0 6px 14px rgba(0, 0, 0, 0.05);
  transition: transform 0.3s ease, box-shadow 0.3s ease;
  min-width: 230px;
  font-size: 0.95rem;
  color: #2c3e50;
  font-weight: 500;
}
.skill-item:hover {
  transform: translateY(-6px);
  box-shadow: 0 12px 24px rgba(0, 0, 0, 0.1);
  background: #eef4f8;
}

.skill-icon {
  width: 28px;
  height: 28px;
  object-fit: contain;
  filter: drop-shadow(0 1px 1px rgba(0, 0, 0, 0.1));
}

</style>
