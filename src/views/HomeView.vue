<template>
  <div class="min-h-screen bg-gray-50 py-12 px-4 sm:px-6 lg:px-8">
    <div class="max-w-7xl mx-auto">
      <div class="grid grid-cols-1 md:grid-cols-2 gap-8">
        <div class="bg-white p-6 rounded-lg shadow-md">
          <h2 class="text-3xl font-bold text-gray-900 mb-4">Welcome to My Portfolio</h2>
          <p class="text-gray-600 mb-6">I'm a passionate frontend developer specializing in Vue.js and modern web technologies.</p>
          <button @click="goToProjects" class="bg-blue-600 text-white px-6 py-2 rounded-md hover:bg-blue-700 transition-colors">
            View My Projects
          </button>
        </div>
        <div class="bg-white p-6 rounded-lg shadow-md">
          <h3 class="text-2xl font-semibold text-gray-900 mb-4">Latest Work</h3>
          <div class="relative h-96">
            <div class="absolute inset-0 overflow-hidden">
              <div class="flex transition-transform duration-500 ease-in-out" :style="{ transform: `translateX(-${currentIndex * 100}%)` }">
                <div v-for="(project, index) in projects" :key="project.id" class="flex-1">
                  <div class="h-full flex items-center justify-center">
                    <h3 class="text-xl font-semibold text-gray-900">{{ project.title }}</h3>
                  </div>
                </div>
              </div>
            </div>
            <button @click="prevSlide" class="absolute left-4 top-1/2 -translate-y-1/2 bg-white rounded-full p-2 shadow-md hover:bg-gray-100 transition-colors">
              <svg class="w-5 h-5 text-gray-600" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M15 19l-7-7 7-7"/>
              </svg>
            </button>
            <button @click="nextSlide" class="absolute right-4 top-1/2 -translate-y-1/2 bg-white rounded-full p-2 shadow-md hover:bg-gray-100 transition-colors">
              <svg class="w-5 h-5 text-gray-600" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9 5l7 7-7 7"/>
              </svg>
            </button>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref, onMounted } from 'vue'
import { useRouter } from 'vue-router'

const router = useRouter()
const projects = ref([
  { id: 1, title: 'Project 1' },
  { id: 2, title: 'Project 2' },
  { id: 3, title: 'Project 3' }
])

const currentIndex = ref(0)
const interval = ref(null)

const goToProjects = () => {
  router.push('/projects')
}

const nextSlide = () => {
  currentIndex.value = (currentIndex.value + 1) % projects.value.length
}

const prevSlide = () => {
  currentIndex.value = (currentIndex.value - 1 + projects.value.length) % projects.value.length
}

onMounted(() => {
  interval.value = setInterval(() => {
    nextSlide()
  }, 4000)
})

</script>

<style scoped>
/* No styles needed, using Tailwind CSS classes */
</style>