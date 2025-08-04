<template>
  <footer class="footer">
    <div class="footer-container">
      <p class="footer-text">
        © {{ currentYear }} Jose Enrique Corea Cruz – Todos los derechos reservados.
      </p>
      <p class="footer-creator">
        Sitio desarrollado por
        <a
          href="https://www.linkedin.com/in/andres-david-gutierrez-corales-1558632a2/"
          target="_blank"
          rel="noopener"
        >
          Andrés David Gutiérrez Corales
        </a>
      </p>
      <p class="footer-icons">
        Iconos proporcionados por
        <a
          href="https://iconos8.es/"
          target="_blank"
          rel="noopener"
        >
          Icons8
        </a>
      </p>
    </div>
  </footer>
</template>

<script>
export default {
  name: "FooterComponent",
  data() {
    return {
      currentYear: new Date().getFullYear(),
    };
  },
};
</script>

<style scoped>
.footer {
  background: #2c3e50;
  color: #ecf0f1;
  text-align: center;
  padding: 2rem 1rem;
  margin-top: 4rem;
  animation: fadeIn 1s ease;
}
.footer-container {
  max-width: 1200px;
  margin: auto;
}
.footer-text,
.footer-creator,
.footer-icons {
  margin: 0.3rem 0;
  font-size: 0.95rem;
}
.footer-creator a,
.footer-icons a {
  color: #1abc9c;
  text-decoration: none;
  font-weight: 600;
  transition: color 0.3s;
}
.footer-creator a:hover,
.footer-icons a:hover {
  color: #16a085;
}
@keyframes fadeIn {
  from {
    opacity: 0;
    transform: translateY(20px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}
</style>
