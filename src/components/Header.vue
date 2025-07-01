<template>
  <nav class="header">
    <div class="nav-wrapper">
      <div class="logo">
        <router-link to="/" class="logo-link">
          <h1>Portfolio</h1>
        </router-link>
      </div>
      <div class="nav-links">
        <router-link to="/" class="nav-item">Home</router-link>
        <router-link to="/about" class="nav-item">About</router-link>
        <router-link to="/projects" class="nav-item">Projects</router-link>
        <router-link to="/contact" class="nav-item">Contact</router-link>
      </div>
      <div class="mobile-menu" @click="toggleMobileMenu">
        <span v-if="!isMobileMenuOpen" class="menu-icon">☰</span>
        <span v-else class="close-icon">×</span>
      </div>
    </div>
    <div v-if="isMobileMenuOpen" class="mobile-nav-links">
      <router-link to="/" class="nav-item" @click="toggleMobileMenu">Home</router-link>
      <router-link to="/about" class="nav-item" @click="toggleMobileMenu">About</router-link>
      <router-link to="/projects" class="nav-item" @click="toggleMobileMenu">Projects</router-link>
      <router-link to="/contact" class="nav-item" @click="toggleMobileMenu">Contact</router-link>
    </div>
  </nav>
</template>

<script setup>
import { ref } from 'vue'
import { useRouter } from 'vue-router'

const router = useRouter()
const isMobileMenuOpen = ref(false)

const toggleMobileMenu = () => {
  isMobileMenuOpen.value = !isMobileMenuOpen.value
}

// Close mobile menu when navigating to a new route
router.afterEach(() => {
  isMobileMenuOpen.value = false
})
</script>

<style scoped>
.header {
  background-color: #ffffff;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
  position: fixed;
  width: 100%;
  top: 0;
  z-index: 1000;
  padding: 1rem 2rem;
}

.nav-wrapper {
  display: flex;
  justify-content: space-between;
  align-items: center;
  max-width: 1200px;
  margin: 0 auto;
}

.logo {
  font-size: 1.5rem;
  font-weight: bold;
  color: #2c3e50;
}

.logo-link {
  text-decoration: none;
  color: #2c3e50;
}

.nav-links {
  display: flex;
  gap: 2rem;
}

.nav-item {
  text-decoration: none;
  color: #2c3e50;
  font-weight: 500;
  transition: color 0.3s ease;
}

.nav-item:hover {
  color: #3498db;
}

.mobile-menu {
  display: none;
  font-size: 1.5rem;
  cursor: pointer;
}

.mobile-nav-links {
  display: none;
  position: absolute;
  top: 100%;
  left: 0;
  right: 0;
  background-color: #ffffff;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
  padding: 1rem;
  flex-direction: column;
  gap: 1rem;
}

@media (max-width: 768px) {
  .nav-links {
    display: none;
  }
  
  .mobile-menu {
    display: block;
  }
  
  .mobile-nav-links {
    display: flex;
  }
}
</style>
