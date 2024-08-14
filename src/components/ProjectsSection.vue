<template>
  <main>
    <div class="tituloHabilidades">
      <h1>Habilidades</h1>
    </div>
    <div class="titulo-inicio">
      <p>Html</p>
      <!--Se llama a toggleContent pasando el nombre de la sección correspondiente-->
      <button class="botonverMas">Certificado</button>
    </div>

    <div class="titulo-inicio">
      <p>CSS</p>
      <button class="botonverMas">Certificado</button>
    </div>
  </main>
</template>

<script>
const show = ref(true);
import { FontAwesomeIcon } from "@fortawesome/vue-fontawesome";
import Carousel from "@/components/Carousel.vue";
import { ref } from "vue";
import { faArrowLeft } from "@fortawesome/free-solid-svg-icons";
import { library } from "@fortawesome/fontawesome-svg-core";
import { faMagnifyingGlass } from "@fortawesome/free-solid-svg-icons";

export default {
  name: "ProjectsSection",
  components: {
    FontAwesomeIcon,
    Carousel,
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
  width: 100%;
}

.tituloHabilidades {
  display: flex;
  position: relative;
  margin-bottom: 15px;
}

.titulo-inicio {
  display: flex;
  flex-direction: column;
  border: 1px solid;
  align-items: center;
  text-align: center;
  width: 400px;
  color: white;
  margin-top: 80px;
}

.titulo-inicio p {
  font-size: 40px;
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

.carruselPrincipal {
  position: absolute;
  top: 60px;
  transform: translateX(600px);
}
</style>
