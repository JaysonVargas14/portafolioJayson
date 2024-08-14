<template>
  <div class="containerPrincipal">
    <TitleSection></TitleSection>
<<<<<<< HEAD
<<<<<<< HEAD
    <MedioSection></MedioSection>
    <ProjectSection></ProjectSection>
=======
    <div class="divider"></div>
    <MedioSection></MedioSection>
    <ProjectsSection></ProjectsSection>
>>>>>>> master
=======
    <MedioSection></MedioSection>
    <ProjectSection></ProjectSection>
>>>>>>> 6d7956a (Se han implementado cambios en el componente MedioSection, puesto que se han agregado e individualizado los 3 componentes de secciones Sobre mi, experiencia y habilidades. Modificación de estilos y lógica.)
  </div>
</template>

<!--Mala práctica: <script src="../view-logic/Home.js"></script>
-->

<script>
import Home from "../view-logic/Home.js";

import TitleSection from "../components/TitleSection.vue";
<<<<<<< HEAD
<<<<<<< HEAD
import MedioSection from "@/components/MedioSection.vue";
=======
import MedioSection from "@/components/MedioSection/MedioSection.vue";
import ProjectsSection from "@/components/ProjectsSection.vue";
>>>>>>> master
=======
import MedioSection from "@/components/MedioSection.vue";
>>>>>>> 6d7956a (Se han implementado cambios en el componente MedioSection, puesto que se han agregado e individualizado los 3 componentes de secciones Sobre mi, experiencia y habilidades. Modificación de estilos y lógica.)
import Carousel from "@/components/Carousel.vue";
import ProjectSection from "@/components/ProjectSection.vue";

export default {
  components: {
    TitleSection,
    MedioSection,
<<<<<<< HEAD
<<<<<<< HEAD
    ProjectSection,
=======
    ProjectsSection,
>>>>>>> master
=======
    ProjectSection,
>>>>>>> 6d7956a (Se han implementado cambios en el componente MedioSection, puesto que se han agregado e individualizado los 3 componentes de secciones Sobre mi, experiencia y habilidades. Modificación de estilos y lógica.)
    Carousel,
  },
};
</script>

<style scoped>
.containerPrincipal {
  flex-direction: column;
  margin-bottom: 50px;
  width: 100%;
  height: 100%; /* Asegura que el contenedor ocupe la altura completa de la ventana */
  color: white; /* Asegura que el texto sea visible sobre la imagen de fondo */
}

.containerPrincipal > * {
  /** Aplican espacio con el * a cada hijo de containerPrincipal/ */
  margin-top: 200px; /* Espacio entre cada componente */
}
</style>
