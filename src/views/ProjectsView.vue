<template>
  <div class="projects">
    <el-row :gutter="20" class="mt-4">
      <el-col :span="24">
        <h1 class="text-center mb-4">My Projects</h1>
      </el-col>
      <el-col :span="24">
        <el-tabs type="border-card">
          <el-tab-pane label="Featured Projects">
            <el-row :gutter="20">
              <el-col :span="8" v-for="project in featuredProjects" :key="project.id">
                <el-card>
                  <template #header>
                    <div class="card-header">
                      <span>{{ project.title }}</span>
                      <el-tag type="success" class="ml-2">{{ project.tech }}</el-tag>
                    </div>
                  </template>
                  <div class="text item">
                    <p>{{ project.description }}</p>
                    <div class="project-links mt-2">
                      <el-button type="text" @click="openLink(project.demo)" v-if="project.demo">
                        <el-icon><Link /></el-icon> Live Demo
                      </el-button>
                      <el-button type="text" @click="openLink(project.code)" v-if="project.code">
                        <el-icon><Link /></el-icon> Source Code
                      </el-button>
                    </div>
                  </div>
                </el-card>
              </el-col>
            </el-row>
          </el-tab-pane>
          <el-tab-pane label="All Projects">
            <el-row :gutter="20">
              <el-col :span="8" v-for="project in allProjects" :key="project.id">
                <el-card>
                  <template #header>
                    <div class="card-header">
                      <span>{{ project.title }}</span>
                      <el-tag type="success" class="ml-2">{{ project.tech }}</el-tag>
                    </div>
                  </template>
                  <div class="text item">
                    <p>{{ project.description }}</p>
                    <div class="project-links mt-2">
                      <el-button type="text" @click="openLink(project.demo)" v-if="project.demo">
                        <el-icon><Link /></el-icon> Live Demo
                      </el-button>
                      <el-button type="text" @click="openLink(project.code)" v-if="project.code">
                        <el-icon><Link /></el-icon> Source Code
                      </el-button>
                    </div>
                  </div>
                </el-card>
              </el-col>
            </el-row>
          </el-tab-pane>
        </el-tabs>
      </el-col>
    </el-row>
  </div>
</template>

<script setup>
import { ref } from 'vue'
import { Link } from '@element-plus/icons-vue'

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

<style scoped>
.project-links {
  display: flex;
  gap: 1rem;
}
</style>
