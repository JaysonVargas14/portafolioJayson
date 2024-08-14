<template>
  <div class="section">
    <transition name="fade">
      <div v-if="isVisible" class="section-content">
        <h1>Habilidades</h1>
        <button class="botonverMas" @click="toggleSection">
          {{ isCurrentSection ? "Ver menos" : "Ver más" }}
        </button>
        <transition name="fade">
          <ul v-if="isCurrentSection" class="descripcion">
            <li>Vue.js</li>
            <li>Bootstrap</li>
            <li>Javascript</li>
            <li>Voiceflow</li>
          </ul>
        </transition>
      </div>
    </transition>
  </div>
</template>

<script>
import { ref } from "vue";

export default {
  name: "habilidades",
  props: {
    currentSection: {
      type: String,
      required: true,
    },
  },
  computed: {
    isCurrentSection() {
      return this.currentSection === "habilidades";
    },
    isVisible() {
      return this.currentSection === "" || this.isCurrentSection;
    },
  },
  methods: {
    toggleSection() {
      this.$emit("toggleSection", "habilidades");
    },
  },
  setup() {
    const showContent = ref({
      experiencia: false,
      sobreMi: false,
      hola: false,
    });

    /**Aquí, recibe el nombre de la sección como argumento y cambia el estado true a false o viceversa */
    const toggleContent = (section) => {
      showContent.value[section] = !showContent.value[section];
    };
    return { showContent, toggleContent };
  },
};
</script>

<style scoped>
.section {
  margin: 20px 0;
  padding: 20px;
  display: flex;
  text-align: center;
}

.section h1 {
  font-size: 60px;
  margin: 0;
}

.fade-enter-active,
.fade-leave-active {
  transition: opacity 0.5s ease-in-out;
}
.fade-enter-from,
.fade-leave-to {
  opacity: 0;
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
</style>
