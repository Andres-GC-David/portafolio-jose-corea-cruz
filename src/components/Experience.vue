<template>
  <section class="experience-section">
    <div class="container">
      <h2 class="section-title">Experiencia Profesional</h2>
      <div class="timeline">
        <div v-for="(job, index) in experiences" :key="index" class="timeline-item">
          <div class="timeline-icon">
            <img :src="getIcon(job.icon)" alt="icon" />
          </div>
          <div class="timeline-content" :class="{ 'left': index % 2 === 0, 'right': index % 2 !== 0 }">
            <h3 class="job-title">{{ job.title }}</h3>
            <h4 class="company">{{ job.company }}</h4>
            <p class="date">{{ job.period }}</p>
            <ul>
              <li v-for="(point, idx) in job.details" :key="idx">{{ point }}</li>
            </ul>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  name: 'Experience',
  data() {
    return {
      experiences: [
        {
          title: "Supervisor de Proyectos",
          company: "Arconsa Constructora - Hotel Andaz",
          period: "2024",
          icon: "supervisor.png",
          details: [
            "Remodelación simultánea de cinco áreas clave.",
            "Coordinación de contratistas y compras de materiales.",
            "Supervisión de estándares constructivos.",
            "Elaboración de planos y gestión de comunicación técnica."
          ]
        },
        {
          title: "Modelador MEP",
          company: "Edica Constructora - Nekajui Ritz",
          period: "2024",
          icon: "mepproject.png",
          details: [
            "Modelado MEP para instalaciones de piscinas.",
            "Revisión de diseño para eficiencia y compatibilidad.",
            "Trabajo en Revit con estándares técnicos exigentes."
          ]
        },
        {
          title: "Supervisor de Remodelaciones",
          company: "Arconsa Constructora - Hotel Andaz",
          period: "2025",
          icon: "remodel.png",
          details: [
            "Supervisión de múltiples frentes en remodelaciones.",
            "Gestión de contratistas y compras.",
            "Participación en áreas de spa, habitaciones y Río Bhongo F2.",
            "Comunicación efectiva entre equipos multidisciplinarios."
          ]
        },
        {
          title: "Control de Planillas",
          company: "Arconsa Constructora",
          period: "2025 - Actual",
          icon: "planillas.png",
          details: [
            "Seguimiento y control de planillas de personal.",
            "Optimización del manejo de recursos humanos."
          ]
        }
      ]
    };
  },
  methods: {
    getIcon(filename) {
      return new URL(`../assets/icons/${filename}`, import.meta.url).href;
    },
  },
};
</script>

<style scoped>
.experience-section {
  background: linear-gradient(to right, #f5f7fa, #e5edf3);
  padding: 5rem 1rem;
}
.container {
  max-width: 1100px;
  margin: 0 auto;
}
.section-title {
  text-align: center;
  font-size: 2.7rem;
  color: #2c3e50;
  margin-bottom: 3rem;
  animation: fadeIn 1s ease forwards;
}

/* Timeline */
.timeline {
  position: relative;
  margin: 2rem 0;
  padding-left: 2rem;
  border-left: 4px solid #2c3e50;
}
.timeline-item {
  position: relative;
  margin-bottom: 4rem;
}
.timeline-icon {
  position: absolute;
  left: -34px;
  top: 0;
  background: #fff;
  border: 2px solid #2c3e50;
  border-radius: 50%;
  width: 48px;
  height: 48px;
  display: flex;
  justify-content: center;
  align-items: center;
  animation: popIn 0.6s ease;
}
.timeline-icon img {
  width: 24px;
  height: 24px;
}
.timeline-content {
  background: white;
  padding: 1.5rem;
  border-radius: 12px;
  box-shadow: 0 12px 24px rgba(0, 0, 0, 0.08);
  animation: fadeInUp 0.8s ease forwards;
  transform: translateY(30px);
  opacity: 0;
}
.timeline-content.left {
  margin-left: 2rem;
}
.timeline-content.right {
  margin-left: 2rem;
}

.job-title {
  font-size: 1.5rem;
  color: #34495e;
  margin-bottom: 0.2rem;
}
.company {
  font-size: 1rem;
  color: #7f8c8d;
  margin-bottom: 0.5rem;
}
.date {
  font-size: 0.9rem;
  color: #95a5a6;
  margin-bottom: 1rem;
}
.timeline-content ul {
  padding-left: 1.2rem;
}
.timeline-content li {
  font-size: 0.95rem;
  line-height: 1.6;
  color: #2c3e50;
}

/* Animations */
@keyframes fadeInUp {
  to {
    transform: translateY(0);
    opacity: 1;
  }
}
@keyframes fadeIn {
  from {
    opacity: 0;
    transform: scale(0.95);
  }
  to {
    opacity: 1;
    transform: scale(1);
  }
}
@keyframes popIn {
  from {
    transform: scale(0);
  }
  to {
    transform: scale(1);
  }
}

/* Responsive */
@media (max-width: 768px) {
  .timeline {
    padding-left: 1rem;
  }
  .timeline-content {
    margin-left: 2rem !important;
  }
}
</style>
