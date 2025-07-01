<template>
  <nav class="fixed w-full bg-white shadow-sm z-50">
    <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
      <div class="flex justify-between h-16">
        <div class="flex">
          <router-link to="/" class="flex items-center">
            <h1 class="text-xl font-bold text-gray-900">Portfolio</h1>
          </router-link>
        </div>
        <div class="hidden sm:flex items-center space-x-8">
          <router-link to="/" class="text-gray-600 hover:text-blue-600 transition-colors">Home</router-link>
          <router-link to="/about" class="text-gray-600 hover:text-blue-600 transition-colors">About</router-link>
          <router-link to="/projects" class="text-gray-600 hover:text-blue-600 transition-colors">Projects</router-link>
          <router-link to="/contact" class="text-gray-600 hover:text-blue-600 transition-colors">Contact</router-link>
        </div>
        <div class="flex items-center sm:hidden">
          <button @click="toggleMobileMenu" class="text-gray-500 hover:text-gray-600 focus:outline-none focus:text-gray-600">
            <svg v-if="!isMobileMenuOpen" class="h-6 w-6" fill="none" stroke="currentColor" viewBox="0 0 24 24">
              <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4 6h16M4 12h16M4 18h16" />
            </svg>
            <svg v-else class="h-6 w-6" fill="none" stroke="currentColor" viewBox="0 0 24 24">
              <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M6 18L18 6M6 6l12 12" />
            </svg>
          </button>
        </div>
      </div>
    </div>

    <div v-if="isMobileMenuOpen" class="sm:hidden">
      <div class="px-2 pt-2 pb-3 space-y-1">
        <router-link to="/" @click="toggleMobileMenu" class="block px-3 py-2 text-gray-600 hover:text-blue-600 transition-colors">Home</router-link>
        <router-link to="/about" @click="toggleMobileMenu" class="block px-3 py-2 text-gray-600 hover:text-blue-600 transition-colors">About</router-link>
        <router-link to="/projects" @click="toggleMobileMenu" class="block px-3 py-2 text-gray-600 hover:text-blue-600 transition-colors">Projects</router-link>
        <router-link to="/contact" @click="toggleMobileMenu" class="block px-3 py-2 text-gray-600 hover:text-blue-600 transition-colors">Contact</router-link>
      </div>
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
