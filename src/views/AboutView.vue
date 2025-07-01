<template>
  <div class="min-h-screen bg-gray-50 py-12 px-4 sm:px-6 lg:px-8">
    <div class="max-w-7xl mx-auto">
      <div class="grid grid-cols-1 md:grid-cols-2 gap-8">
        <div class="bg-white p-6 rounded-lg shadow-md">
          <h2 class="text-2xl font-semibold text-gray-900 mb-4">Skills</h2>
          <div class="space-y-2">
            <span v-for="skill in skills" :key="skill.name" 
                  :class="[
                    'inline-flex items-center px-3 py-1 rounded-full text-sm font-medium',
                    skill.type === 'success' ? 'bg-green-100 text-green-800' :
                    skill.type === 'info' ? 'bg-blue-100 text-blue-800' :
                    skill.type === 'warning' ? 'bg-yellow-100 text-yellow-800' :
                    skill.type === 'danger' ? 'bg-red-100 text-red-800' : ''
                  ]">
              {{ skill.name }}
            </span>
          </div>
        </div>
        <div class="bg-white p-6 rounded-lg shadow-md">
          <h2 class="text-3xl font-bold text-gray-900 mb-6">About Me</h2>
          <p class="text-gray-600 mb-8">I'm a frontend developer with a passion for creating beautiful and functional web applications. I specialize in Vue.js and modern web technologies.</p>
          <div class="space-y-6">
            <div v-for="(activity, index) in activities" :key="index" class="relative">
              <div class="absolute -left-3 top-0 h-full w-px bg-gray-200"></div>
              <div class="pl-6">
                <div class="flex items-start space-x-4">
                  <div class="flex-shrink-0">
                    <div class="h-10 w-10 rounded-full bg-gray-200 flex items-center justify-center">
                      <svg class="h-6 w-6 text-gray-600" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                        <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M12 8v4l3 3m6-3a9 9 0 11-18 0 9 9 0 0118 0z"/>
                      </svg>
                    </div>
                  </div>
                  <div class="flex-1 min-w-0">
                    <h3 class="text-lg font-semibold text-gray-900">{{ activity.title }}</h3>
                    <p class="text-sm text-gray-500">{{ activity.timestamp }}</p>
                    <p class="mt-2 text-gray-600">{{ activity.description }}</p>
                  </div>
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

const skills = ref([
  { name: 'Vue.js', type: 'success' },
  { name: 'JavaScript', type: 'info' },
  { name: 'HTML/CSS', type: 'warning' },
  { name: 'Tailwind CSS', type: 'danger' },
  { name: 'Element Plus', type: 'success' }
])

const activities = ref([
  { title: 'Frontend Developer', timestamp: '2023 - Present', description: 'Working on various Vue.js projects' },
  { title: 'Web Developer', timestamp: '2022 - 2023', description: 'Learning and implementing modern web technologies' },
  { title: 'Intern', timestamp: '2021 - 2022', description: 'Starting my journey in web development' }
])
</script>

<style scoped>
/* No styles needed, using Tailwind CSS classes */
</style>