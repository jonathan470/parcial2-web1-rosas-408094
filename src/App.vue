<template>
  <div class="layout">
    <!-- HEADER -->
    <header class="layout__header">
      <img
        src="./assets/logo-removebg-preview (4).png"
        alt="Logo"
        class="layout__logo"
      />
      <h1 class="layout__title">Mi Perfil</h1>
      <input type="search" class="layout__search" placeholder="Buscar..." />
    </header>

    <!-- MAIN -->
    <main class="layout__main">
      <div class="main__wrapper">
        <!-- ASIDE -->
        <aside class="profile">
          <img
            src="./assets/Avartar-removebg-preview.png"
            alt="Foto de perfil"
            class="profile__avatar"
          />
          <h2 class="profile__name">Jonathan</h2>
          <p class="profile__bio">
            Desarrollador web apasionado por el diseño y la tecnología.
          </p>

          <h3 class="profile__friends-title">Amigos</h3>
          <div class="profile__friends">
            <div class="profile__friend" v-for="n in 6" :key="n"></div>
          </div>
        </aside>

        <!-- CONTENIDO PRINCIPAL -->
        <section class="main__content">
          <!-- NAVIGATION -->
          <nav class="nav">
            <button
              v-for="link in links"
              :key="link"
              @click="currentView = link"
              class="nav__link"
              :class="{ active: currentView === link }"
            >
              {{ link.charAt(0).toUpperCase() + link.slice(1) }}
            </button>
          </nav>

          <!-- CONTENIDO HIJO -->
          <section class="content">
            <component :is="componentsMap[currentView]" />
          </section>
        </section>
      </div>
    </main>

    <!-- FOOTER -->
    <footer class="layout__footer">
      <p class="layout__footer-text">© 2025 Jonathan SPA</p>
    </footer>
  </div>
</template>

<script setup>
import { ref } from "vue";
import Home from "./components/children-home.vue";
import About from "./components/children-about.vue";
import Photos from "./components/children-photos.vue";
import Boxes from "./components/children-boxes.vue";

// estado reactivo (qué hijo está activo)
const currentView = ref("home");

// mapa de componentes hijos
const componentsMap = {
  home: Home,
  about: About,
  photos: Photos,
  boxes: Boxes,
};

// enlaces del menú
const links = ["home", "about", "photos", "boxes"];

</script>

<style scoped>
.layout {
  display: flex;
  flex-direction: column;
  min-height: 100vh;
}

.layout__header {
  display: flex;
  align-items: center;
  justify-content: space-between;
  background-color: #4267b2;
  color: white;
  padding: 1rem 2rem;
}

.layout__logo {
  height: 40px;
}

.layout__title {
  font-size: 1.5rem;
  margin-left: 1rem;
}

.layout__search {
  padding: 0.5rem;
  border-radius: 4px;
  border: none;
  width: 200px;
}

.layout__main {
  flex: 1;
}

.main__wrapper {
  display: flex;
  gap: 2rem;
  padding: 2rem;
}

.profile {
  width: 250px;
  background-color: #e4e6eb;
  padding: 1rem;
  border-radius: 8px;
  box-shadow: 0 1px 4px rgba(0, 0, 0, 0.1);
}

.profile__avatar {
  width: 100px;
  height: 100px;
  border-radius: 50%;
  object-fit: cover;
  margin-bottom: 1rem;
}

.profile__name {
  font-size: 1.2rem;
  margin-bottom: 0.5rem;
}

.profile__bio {
  font-size: 0.95rem;
  color: #555;
  margin-bottom: 1rem;
}

.profile__friends-title {
  font-size: 1rem;
  margin-bottom: 0.5rem;
}

.profile__friends {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 0.5rem;
}

.profile__friend {
  width: 60px;
  height: 60px;
  background-color: #b6bac2;
  border-radius: 8px;
}

.main__content {
  flex: 1;
}

.nav {
  display: flex;
  justify-content: center;
  background-color: #e9ebee;
  padding: 1rem;
  gap: 1rem;
}

.nav__link {
  text-decoration: none;
  color: #333;
  font-weight: bold;
  padding: 0.5rem 1rem;
  border-radius: 4px;
  transition: background-color 0.3s ease;
}

.nav__link:hover {
  background-color: #d8dfea;
  color: #4267b2;
}

.content {
  padding: 2rem;
}

.layout__footer {
  background-color: #e9ebee;
  text-align: center;
  padding: 1rem;
}

.layout__footer-text {
  font-size: 0.9rem;
  color: #666;
}
</style>
