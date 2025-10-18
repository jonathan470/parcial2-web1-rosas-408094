<template>
  <section class="content__section">
    <h2 class="content__title">Fotos</h2>
    <div class="content__grid">
      <div class="content__box">📸 Viaje a Medellín</div>
      <div class="content__box">🌄 Sendero en el Parque Nacional</div>
      <div class="content__box">🎓 Graduación</div>
      <div class="content__box">🎮 Torneo de videojuegos</div>
    </div>
  </section>
</template>

<script>

</script>


<style scoped>
.content__section {
  max-width: 800px;
  margin: auto;
}

.content__title {
  font-size: 2rem;
  margin-bottom: 1rem;
  color: #333;
}
.content__grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(150px, 1fr));
  gap: 1rem;
  margin-top: 1rem;
}

.content__box {
  background-color: #e4e6eb;
  padding: 1rem;
  text-align: center;
  border-radius: 8px;
  font-size: 1rem;
  color: #333;
  box-shadow: 0 2px 4px rgba(0,0,0,0.1);
}

</style>