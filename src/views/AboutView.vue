<template>
    <div class="about">
      <el-row :gutter="20" class="mt-4">
        <el-col :span="8">
          <el-card>
            <template #header>
              <div class="card-header">
                <span>Skills</span>
              </div>
            </template>
            <el-tag v-for="skill in skills" :key="skill" :type="skill.type" class="m-2">
              {{ skill.name }}
            </el-tag>
          </el-card>
        </el-col>
        <el-col :span="16">
          <el-card>
            <template #header>
              <div class="card-header">
                <span>About Me</span>
              </div>
            </template>
            <div class="text item">
              <p>I'm a frontend developer with a passion for creating beautiful and functional web applications. I specialize in Vue.js and modern web technologies.</p>
              <el-timeline>
                <el-timeline-item v-for="(activity, index) in activities" :key="index" :timestamp="activity.timestamp" placement="top">
                  <el-card>
                    <h4>{{ activity.title }}</h4>
                    <p>{{ activity.description }}</p>
                  </el-card>
                </el-timeline-item>
              </el-timeline>
            </div>
          </el-card>
        </el-col>
      </el-row>
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