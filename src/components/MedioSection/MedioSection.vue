<template>
  <main>
    <transition-group name="fade" tag="div" class="grid-container">
      <div
        v-if="currentSection === '' || currentSection === 'experience'"
        :key="'experience-' + currentSection"
        :class="[
          'titulo-inicio',
          {
            focus: currentSection === 'experience',
            'move-right': currentSection === 'experience' && isExpanded,
            'move-left': currentSection === 'experience' && !isExpanded,
          },
        ]"
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
        :class="[
          'titulo-inicio',
          {
            focus: currentSection === 'sobreMi',
            'move-right': currentSection === 'sobreMi' && isExpanded,
            'move-left': currentSection === 'sobreMi' && !isExpanded,
          },
        ]"
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
        :class="[
          'titulo-inicio',
          {
            focus: currentSection === 'habilidades',
            'move-right': currentSection === 'habilidades' && isExpanded,
            'move-left': currentSection === 'habilidades' && !isExpanded,
          },
        ]"
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
const show = ref(true);
import { FontAwesomeIcon } from "@fortawesome/vue-fontawesome";
import Carousel from "@/components/Carousel.vue";
import { ref } from "vue";
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
          // Si se hace clic en "Ver menos", se espera un pequeño tiempo antes de colapsar el componente
          setTimeout(() => {
            currentSection.value = "";
          }, 500); // Ajusta el tiempo para que coincida con la animación
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
  grid-template-columns: repeat(3, 1fr); /* Dos columnas de igual tamaño */
  gap: 10px; /* Espacio entre los elementos */
  height: 50vh;
  justify-content: center;
}

.titulo-inicio {
  /** Crear 3 componentes, cada uno tiene su animación individual, pero cada componente que tenga una transición de entrada */
  display: flex;
  flex-direction: column;
  justify-content: flex-start; /* Centra el contenido verticalmente */
  align-items: center;
  text-align: center;
  width: 400px;
  color: white;
  margin-top: 150px;
  position: relative;
  transform: translateX(-10%); /*Centrado */
  transition: transform 0.5s ease-in-out;
}

.titulo-inicio.focus {
  animation: focusAnimation 2s ease forwards;
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

.move-right {
  transform: translateX(
    100%
  ); /* Mueve el componente seleccionado a la derecha */
}

.move-left {
  transform: translateX(
    0
  ); /* Retorna el componente seleccionado a su posición original */
}

.titulo-inicio h1 {
  font-size: 60px;
  margin: 0;
}

.botones-container {
  display: flex;
  justify-content: center;
  align-items: center;
  gap: 10px; /* Espacio entre los botones */
}

.botonverMas {
  position: relative;
  justify-content: space-between;
  border: none;
  width: 300px;
  padding: 15px;
  background-color: var(--color-verde);
  color: var(--color-blanco);
  cursor: pointer;
  margin-top: 10px; /* Espacio entre el título y el botón */
}

.botonVerMas,
.botonverMas span {
  transition: 0.4s ease-in-out all;
  position: relative;
  justify-content: center;
  text-align: center;
  right: 0%;
}

.botonVerMas,
.botonverMas .icono {
  display: flex;
  align-items: center;
  position: absolute;
  z-index: 2;
  left: -20px;
  transition: 0.3 ease-in-out all;
  opacity: 0;
}

.botonVerMas,
.botonverMas svg {
  color: var(--color-blanco);
  width: 35px;
  height: 35px;
}

.botonverMas:hover {
  background-color: var(--color-verde-hover);
  transition: 0.5s;
}

.botonVerMas:hover .icono {
  left: calc(100% - 50px);
  opacity: 1;
}

.botonVerMas:hover span {
  right: 50px;
}
.descripcion {
  margin-top: 50px; /* Espacio entre los botones y la descripción */
}

.fade-enter-active,
.fade-leave-active {
  transition: opacity 0.5 ease-in-out;
}

.fade-enter-from,
.fade-leave-to {
  transition: opacity 0.5 ease-in-out;
}

/* Animación de enfoque para el componente seleccionado */
.focus {
  animation: focusAnimation 2s ease forwards; /*Animación de foco poco a poco*/
}

@keyframes focusAnimation {
  0% {
    transform: scale(1) translateY(0); /* Sin cambio en el tamaño o posición inicial */
  }
  50% {
    transform: scale(1.2) translateY(-10px); /* Aumenta el tamaño y eleva ligeramente */
  }
  100% {
    transform: scale(1) translateY(0); /* Tamaño final y posición original */
  }
}

.grid-container {
  display: grid;
  grid-template-columns: repeat(3, 1fr); /* Tres columnas de igual tamaño */
  gap: 10px; /* Espacio entre los elementos */
}

.botonDestino {
  position: relative;
  width: 100%;
  height: 100%;
  border: none;
  padding: 15px;
  background-color: transparent;
  color: var(--color-blanco);
  cursor: pointer;
  margin: 5px 5px 5px 5px;
  transition: 0.3 ease all;
}

.botonDestino span {
  position: relative;
  z-index: 2;
  transition: 0.3s ease all;
}

.botonDestino svg {
  width: 100%;
  height: 100%;
  position: absolute;
  top: 0;
  left: 0;
  fill: none;
}

.botonDestino rect {
  width: 100%;
  height: 50px;
  stroke: var(--color-blanco);
  stroke-width: 2px;
  stroke-dasharray: 1000;
  stroke-dashoffset: 1000;
  transition: 0.6s ease all;
}

.botonDestino:hover rect {
  stroke-dashoffset: 0;
}
</style>
