<template>
    <div class="home">
      <el-row :gutter="20" class="mt-4">
        <el-col :span="12">
          <el-card>
            <template #header>
              <div class="card-header">
                <span>Welcome to My Portfolio</span>
              </div>
            </template>
            <div class="text item">
              <p>I'm a passionate frontend developer specializing in Vue.js and modern web technologies.</p>
              <el-button type="primary" @click="goToProjects">View My Projects</el-button>
            </div>
          </el-card>
        </el-col>
        <el-col :span="12">
          <el-card>
            <template #header>
              <div class="card-header">
                <span>Latest Work</span>
              </div>
            </template>
            <el-carousel :interval="4000" type="card" height="400px">
              <el-carousel-item v-for="item in projects" :key="item.id">
                <h3 text="2xl" justify="center">{{ item.title }}</h3>
              </el-carousel-item>
            </el-carousel>
          </el-card>
        </el-col>
      </el-row>
    </div>
  </template>
  
  <script setup>
  import { ref } from 'vue'
  import { useRouter } from 'vue-router'
  
  const router = useRouter()
  const projects = ref([
    { id: 1, title: 'Project 1' },
    { id: 2, title: 'Project 2' },
    { id: 3, title: 'Project 3' }
  ])
  
  const goToProjects = () => {
    router.push('/projects')
  }
  </script>
  
  <style scoped>
  .card-header {
    display: flex;
    justify-content: space-between;
    align-items: center;
  }
  
  .text {
    font-size: 14px;
  }
  
  .item {
    padding: 18px 0;
  }
  
  .box-card {
    width: 480px;
  }
  </style>