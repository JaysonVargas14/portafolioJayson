<template>
  <main>
    <transition-group name="fade" tag="div" class="grid-container">
      <div
        v-if="currentSection === '' || currentSection === 'experience'"
        :key="'experience-' + currentSection"
        :class="['titulo-inicio', { focus: currentSection === 'experience' }]"
      >
        <Experience
          :currentSection="currentSection"
          sectionName="experience"
          @toggleSection="toggleSection"
        />
      </div>

      <div
        v-if="currentSection === '' || currentSection === 'sobreMi'"
        :key="'sobreMi-' + currentSection"
        :class="['titulo-inicio', { focus: currentSection === 'sobreMi' }]"
      >
        <SobreMi
          :currentSection="currentSection"
          sectionName="sobreMi"
          @toggleSection="toggleSection"
        />
      </div>

      <div
        v-if="currentSection === '' || currentSection === 'habilidades'"
        :key="'habilidades-' + currentSection"
        :class="['titulo-inicio', { focus: currentSection === 'habilidades' }]"
      >
        <Habilidades
          :currentSection="currentSection"
          sectionName="habilidades"
          @toggleSection="toggleSection"
        />
      </div>
    </transition-group>
  </main>
</template>

<script>
import { ref } from "vue";
import { FontAwesomeIcon } from "@fortawesome/vue-fontawesome";
import Carousel from "@/components/Carousel.vue";
import Experience from "./Experience.vue";
import SobreMi from "./SobreMi.vue";
import Habilidades from "./Habilidades.vue";

export default {
  name: "MedioSection",
  components: {
    FontAwesomeIcon,
    Carousel,
    Experience,
    SobreMi,
    Habilidades,
  },
  setup() {
    const currentSection = ref("");
    const isExpanded = ref(false);

    const toggleSection = (section) => {
      if (currentSection.value === section) {
        isExpanded.value = !isExpanded.value;
        if (!isExpanded.value) {
          setTimeout(() => {
            currentSection.value = "";
          }, 200); // Ajusta el tiempo si es necesario
        }
      } else {
        currentSection.value = section;
        isExpanded.value = true;
      }
    };

    return {
      currentSection,
      isExpanded,
      toggleSection,
    };
  },
};
</script>

<style scoped>
body {
  background-color: var(--color-oscuro-fondo2);
}

main {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 10px;
  height: 50vh;
  justify-content: center;
}

.titulo-inicio {
  display: flex;
  flex-direction: column;
  justify-content: flex-start;
  align-items: center;
  text-align: center;
  width: 400px;
  color: white;
  margin-top: 150px;
  position: relative;
  transform: translateX(-10%);
  transition: transform 0.3s ease-in-out, opacity 0.3s ease-in-out;
}

.titulo-inicio.focus {
  animation: focusAnimation 0.2s ease forwards;
}

@keyframes focusAnimation {
  0% {
    transform: scale(1) translateY(0);
  }
  50% {
    transform: scale(1.2) translateY(-10px);
  }
  100% {
    transform: scale(1) translateY(0);
  }
}

.fade-enter-active,
.fade-leave-active {
  transition: opacity 0.3s ease-in-out;
}

.fade-enter-from,
.fade-leave-to {
  opacity: 0;
}

/* Ocultar componentes no activos cuando uno está expandido */
.titulo-inicio:not(.focus) {
  opacity: 0;
  pointer-events: none;
}

.grid-container {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 10px;
}
</style>
