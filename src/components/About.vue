<template>
  <section class="about-section">
    <div class="container">
      <div class="about-content">
        <div class="about-image">
          <img src="/assets/jose-corea-profile-photo.jpeg" alt="Retrato profesional" />
        </div>
        <div class="about-text">
          <h2>Sobre Mí</h2>
          <h3>Arquitecto Resolutivo | Diseñador Estratégico | Disciplinado</h3>
          <p>
            Profesional con dominio en modelado 3D, elaboración
            de planos constructivos y supervisión de obra. Experto
            en coordinación de contratistas, gestión de personal y
            planificación de remodelaciones complejas.
            Comprometido con la calidad, los plazos y la eficiencia
            en cada etapa del proyecto.

          </p>
          <p>
            Además, poseo una sólida experiencia en la evaluación de proyectos 
            para garantizar la viabilidad técnica y financiera. Mi enfoque se centra
            en la resolución de problemas proactiva, implementando soluciones innovadoras
            para superar desafíos inesperados. Mi habilidad para comunicarme eficazmente
            con equipos multidisciplinarios y clientes es clave para asegurar el éxito
            y la satisfacción en cada entrega.
          </p>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  name: "About",
};
</script>

<style scoped>
.about-section {
  padding: 5rem 1rem;
  background: #f9f9f9;
}
.container {
  max-width: 1100px;
  margin: 0 auto;
}
.about-content {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 2rem;
}
.about-image img {
  width: 280px;
  height: auto;
  border-radius: 12px;
  box-shadow: 0 4px 20px rgba(0, 0, 0, 0.2);
}
.about-text {
  max-width: 700px;
  text-align: center;
}
.about-text h2 {
  font-size: 2.5rem;
  margin-bottom: 0.5rem;
  color: #2c3e50;
}
.about-text h3 {
  font-size: 1.3rem;
  font-weight: 500;
  color: #4ca1af;
  margin-bottom: 1.5rem;
}
.about-text p {
  font-size: 1.1rem;
  line-height: 1.8;
  color: #444;
  margin-bottom: 1rem;
}
@media (min-width: 768px) {
  .about-content {
    flex-direction: row;
    align-items: flex-start;
    gap: 3rem;
  }
  .about-text {
    text-align: left;
  }
}
</style>
