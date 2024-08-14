<template>
  <main class="main-container">
    <slot></slot>
    <!-- Aquí se renderizarán los contenidos específicos de cada componente que use este layout -->
  </main>
</template>

<script>
export default {
  name: "MainLayout",
};
</script>

<style scoped>
.main-container {
  display: grid;
  grid-template-columns: 1fr;
  grid-template-rows: auto 1fr auto;
  min-height: 100vh;
}
</style>
