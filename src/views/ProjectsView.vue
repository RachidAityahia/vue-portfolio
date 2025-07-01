<template>
  <div class="projects">
    <div class="max-w-7xl mx-auto px-4">
      <h1 class="text-3xl font-bold text-center mb-8">My Projects</h1>
      
      <div class="tabs">
        <div class="tab-content">
          <div class="featured-projects">
            <div class="grid grid-cols-1 md:grid-cols-3 gap-6">
              <div v-for="project in featuredProjects" :key="project.id" class="project-card">
                <div class="card-header flex justify-between items-center mb-4">
                  <h3 class="text-xl font-semibold">{{ project.title }}</h3>
                  <span class="bg-green-100 text-green-800 px-2 py-1 rounded-full text-sm">{{ project.tech }}</span>
                </div>
                <p class="text-gray-600 mb-4">{{ project.description }}</p>
                <div class="flex gap-4">
                  <button v-if="project.demo" @click="openLink(project.demo)" class="text-blue-600 hover:text-blue-800 flex items-center">
                    <svg class="w-4 h-4 mr-1" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                      <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M10 6H6a2 2 0 00-2 2v10a2 2 0 002 2h10a2 2 0 002-2v-4M14 4h6m0 0v6m0-6L10 14"/>
                    </svg>
                    Live Demo
                  </button>
                  <button v-if="project.code" @click="openLink(project.code)" class="text-blue-600 hover:text-blue-800 flex items-center">
                    <svg class="w-4 h-4 mr-1" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                      <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M10 20l4-16m4 4l4 4-4 4M6 16l-4-4 4-4"/>
                    </svg>
                    Source Code
                  </button>
                </div>
              </div>
            </div>
          </div>

          <div class="all-projects">
            <div class="grid grid-cols-1 md:grid-cols-3 gap-6">
              <div v-for="project in allProjects" :key="project.id" class="project-card">
                <div class="card-header flex justify-between items-center mb-4">
                  <h3 class="text-xl font-semibold">{{ project.title }}</h3>
                  <span class="bg-green-100 text-green-800 px-2 py-1 rounded-full text-sm">{{ project.tech }}</span>
                </div>
                <p class="text-gray-600 mb-4">{{ project.description }}</p>
                <div class="flex gap-4">
                  <button v-if="project.demo" @click="openLink(project.demo)" class="text-blue-600 hover:text-blue-800 flex items-center">
                    <svg class="w-4 h-4 mr-1" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                      <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M10 6H6a2 2 0 00-2 2v10a2 2 0 002 2h10a2 2 0 002-2v-4M14 4h6m0 0v6m0-6L10 14"/>
                    </svg>
                    Live Demo
                  </button>
                  <button v-if="project.code" @click="openLink(project.code)" class="text-blue-600 hover:text-blue-800 flex items-center">
                    <svg class="w-4 h-4 mr-1" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                      <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M10 20l4-16m4 4l4 4-4 4M6 16l-4-4 4-4"/>
                    </svg>
                    Source Code
                  </button>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue'

const featuredProjects = ref([
  {
    id: 1,
    title: 'Portfolio Website',
    tech: 'Vue.js',
    description: 'A modern portfolio website built with Vue.js and Element Plus, featuring responsive design and smooth animations.',
    demo: 'https://example.com/portfolio',
    code: 'https://github.com/yourusername/portfolio'
  },
  {
    id: 2,
    title: 'Task Manager',
    tech: 'Vue.js + Firebase',
    description: 'A real-time task management application that allows users to create, manage, and track their tasks.',
    demo: 'https://example.com/task-manager',
    code: 'https://github.com/yourusername/task-manager'
  },
  {
    id: 3,
    title: 'Weather App',
    tech: 'Vue.js + OpenWeather API',
    description: 'A weather application that provides current weather conditions and forecasts using OpenWeather API.',
    demo: 'https://example.com/weather',
    code: 'https://github.com/yourusername/weather-app'
  }
])

const allProjects = ref([
  ...featuredProjects.value,
  {
    id: 4,
    title: 'E-commerce Store',
    tech: 'Vue.js + Vuex',
    description: 'A complete e-commerce store with shopping cart, product catalog, and user authentication.',
    demo: 'https://example.com/store',
    code: 'https://github.com/yourusername/ecommerce'
  },
  {
    id: 5,
    title: 'Blog Platform',
    tech: 'Vue.js + REST API',
    description: 'A blogging platform with user authentication, post creation, and comment system.',
    demo: 'https://example.com/blog',
    code: 'https://github.com/yourusername/blog'
  }
])

const openLink = (url) => {
  window.open(url, '_blank')
}
</script>


