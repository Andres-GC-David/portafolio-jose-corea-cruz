<template>
  <section class="contact-section">
    <div class="container">
      <h2 class="section-title">Contacto</h2>

      <div class="contact-wrapper">
        <!-- Contact Info -->
        <div class="contact-info">
          <p class="contact-description">
            ¿Tienes un proyecto en mente o deseas colaborar? No dudes en contactarme a través de cualquiera de los siguientes medios:
          </p>

          <div class="info-item">
            <img src="../assets/Call.png" alt="Teléfono" class="icon" />
            <a href="tel:+50684270889">+506 8427-0889</a>
          </div>

          <div class="info-item">
            <img src="../assets/Mail.png" alt="Correo" class="icon" />
            <a href="mailto:Ssjcruz.arq@gmail.com">Ssjcruz.arq@gmail.com</a>
          </div>

          <div class="info-item">
            <img src="../assets/LinkedIn.png" alt="LinkedIn" class="icon" />
            <a href="https://www.linkedin.com/in/jose-cruz-89b21327a/" target="_blank">LinkedIn</a>
          </div>
        </div>

        <!-- Contact Form -->
        <form class="contact-form" @submit.prevent="submitForm">
          <div v-if="success" class="success-message">
            ¡Gracias! Tu mensaje ha sido enviado.
          </div>
          <div class="form-group">
            <label>Nombre</label>
            <input v-model="form.name" type="text" required placeholder="Tu nombre" />
          </div>
          <div class="form-group">
            <label>Correo electrónico</label>
            <input v-model="form.email" type="email" required placeholder="tucorreo@dominio.com" />
          </div>
          <div class="form-group">
            <label>Mensaje</label>
            <textarea v-model="form.message" required placeholder="Escribe tu mensaje aquí..."></textarea>
          </div>
          <button type="submit" class="submit-button" :disabled="submitting">
            {{ submitting ? "Enviando..." : "Enviar mensaje" }}
          </button>
        </form>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  name: "ContactSection",
  data() {
    return {
      form: {
        name: "",
        email: "",
        message: "",
      },
      success: false,
      submitting: false,
      endpoint: "https://formspree.io/f/mpwlyqdw"
    };
  },
  methods: {
    async submitForm() {
      if (this.submitting) return;
      this.submitting = true;
      const payload = new FormData();
      payload.append("name", this.form.name);
      payload.append("email", this.form.email);
      payload.append("message", this.form.message);

      try {
        const resp = await fetch(this.endpoint, {
          method: "POST",
          body: payload,
          headers: { Accept: "application/json" }
        });
        const json = await resp.json();
        if (json.ok || resp.status === 200) {
          this.success = true;
          // clear form
          this.form.name = "";
          this.form.email = "";
          this.form.message = "";
          // hide message after 4s
          setTimeout(() => (this.success = false), 4000);
        } else {
          console.error("Formspree error", json);
          alert("Hubo un error enviando el mensaje.");
        }
      } catch (err) {
        console.error(err);
        alert("Hubo un error de red. Intenta de nuevo.");
      } finally {
        this.submitting = false;
      }
    }
  }
};
</script>

<style scoped>
.contact-section {
  padding: 6rem 1rem;
  background: linear-gradient(to right, #f9f9f9, #e8f1f6);
  animation: fadeIn 1s ease forwards;
}
.container {
  max-width: 1200px;
  margin: auto;
}
.section-title {
  font-size: 2.7rem;
  text-align: center;
  color: #2c3e50;
  margin-bottom: 3rem;
}

.contact-wrapper {
  display: flex;
  flex-wrap: wrap;
  gap: 3rem;
  justify-content: center;
  align-items: flex-start;
  animation: slideUp 1s ease forwards;
}

.contact-info {
  flex: 1 1 300px;
  background: white;
  padding: 2rem;
  border-radius: 16px;
  box-shadow: 0 10px 30px rgba(0, 0, 0, 0.08);
  transition: transform 0.3s ease;
}
.contact-info:hover {
  transform: translateY(-8px);
}
.contact-description {
  font-size: 1.1rem;
  color: #555;
  margin-bottom: 1.5rem;
}
.info-item {
  display: flex;
  align-items: center;
  font-size: 1rem;
  margin-bottom: 1.2rem;
  color: #2c3e50;
}
.icon {
  width: 24px;
  height: 24px;
  margin-right: 0.8rem;
  transition: transform 0.3s;
}
.info-item:hover .icon {
  transform: scale(1.15);
}
.info-item a {
  color: #2c3e50;
  text-decoration: none;
}
.info-item a:hover {
  color: #2980b9;
}

.contact-form {
  flex: 1 1 500px;
  background: white;
  padding: 2rem;
  border-radius: 16px;
  box-shadow: 0 10px 30px rgba(0, 0, 0, 0.08);
  display: flex;
  flex-direction: column;
  gap: 1.5rem;
  transition: transform 0.3s ease;
}
.contact-form:hover {
  transform: translateY(-8px);
}
.form-group {
  display: flex;
  flex-direction: column;
}
.form-group label {
  font-weight: bold;
  margin-bottom: 0.5rem;
  color: #34495e;
}
.form-group input,
.form-group textarea {
  padding: 0.8rem;
  border: 1px solid #ccc;
  border-radius: 12px;
  font-size: 1rem;
  outline: none;
  transition: border 0.3s;
}
.form-group input:focus,
.form-group textarea:focus {
  border-color: #3498db;
}

.submit-button {
  background: linear-gradient(to right, #4ca1af, #2c3e50);
  color: white;
  padding: 0.9rem 1.8rem;
  border: none;
  border-radius: 12px;
  font-size: 1.1rem;
  cursor: pointer;
  transition: background 0.3s, transform 0.2s;
}
.submit-button:hover {
  background: linear-gradient(to right, #2c3e50, #4ca1af);
  transform: translateY(-3px);
}

.success-message {
  background: #4ca1af;
  color: white;
  padding: 1rem;
  border-radius: 8px;
  text-align: center;
  margin-bottom: 1rem;
  animation: fadeIn 0.5s ease;
}

.submit-button[disabled] {
  opacity: 0.6;
  cursor: not-allowed;
}

/* Animations */
@keyframes fadeIn {
  0% {
    opacity: 0;
  }
  100% {
    opacity: 1;
  }
}
@keyframes slideUp {
  0% {
    opacity: 0;
    transform: translateY(30px);
  }
  100% {
    opacity: 1;
    transform: translateY(0);
  }
}

@media (max-width: 768px) {
  .contact-wrapper {
    flex-direction: column;
  }
}
</style>

