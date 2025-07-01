<template>
  <div class="contact">
    <el-row :gutter="20" class="mt-4">
      <el-col :span="24">
        <h1 class="text-center mb-4">Get in Touch</h1>
      </el-col>
      <el-col :span="12" :offset="6">
        <el-card>
          <template #header>
            <div class="card-header">
              <span>Contact Form</span>
            </div>
          </template>
          <el-form :model="form" :rules="rules" ref="formRef" label-width="120px">
            <el-form-item label="Name" prop="name">
              <el-input v-model="form.name" placeholder="Enter your name"></el-input>
            </el-form-item>
            <el-form-item label="Email" prop="email">
              <el-input v-model="form.email" placeholder="Enter your email"></el-input>
            </el-form-item>
            <el-form-item label="Subject" prop="subject">
              <el-input v-model="form.subject" placeholder="Enter subject"></el-input>
            </el-form-item>
            <el-form-item label="Message" prop="message">
              <el-input v-model="form.message" type="textarea" :rows="4" placeholder="Enter your message"></el-input>
            </el-form-item>
            <el-form-item>
              <el-button type="primary" @click="submitForm" :loading="isLoading">Send Message</el-button>
            </el-form-item>
          </el-form>
        </el-card>
      </el-col>
      <el-col :span="24" class="mt-4">
        <el-card>
          <template #header>
            <div class="card-header">
              <span>Contact Information</span>
            </div>
          </template>
          <div class="contact-info">
            <el-row :gutter="20">
              <el-col :span="8">
                <el-card>
                  <el-icon><Location /></el-icon>
                  <p>{{ contactInfo.address }}</p>
                </el-card>
              </el-col>
              <el-col :span="8">
                <el-card>
                  <el-icon><Phone /></el-icon>
                  <p>{{ contactInfo.phone }}</p>
                </el-card>
              </el-col>
              <el-col :span="8">
                <el-card>
                  <el-icon><Message /></el-icon>
                  <p>{{ contactInfo.email }}</p>
                </el-card>
              </el-col>
            </el-row>
          </div>
        </el-card>
      </el-col>
    </el-row>
  </div>
</template>

<script setup>
import { ref, reactive } from 'vue'
import { Location, Phone, Message } from '@element-plus/icons-vue'
import { ElMessage } from 'element-plus'

const formRef = ref(null)
const isLoading = ref(false)

const form = reactive({
  name: '',
  email: '',
  subject: '',
  message: ''
})

const contactInfo = {
  address: '123 Portfolio Street, Web Development City',
  phone: '+1 234 567 890',
  email: 'contact@portfolio.com'
}

const rules = {
  name: [
    { required: true, message: 'Please enter your name', trigger: 'blur' },
    { min: 2, max: 50, message: 'Length should be 2 to 50', trigger: 'blur' }
  ],
  email: [
    { required: true, message: 'Please enter your email', trigger: 'blur' },
    { type: 'email', message: 'Please enter a valid email', trigger: ['blur', 'change'] }
  ],
  subject: [
    { required: true, message: 'Please enter a subject', trigger: 'blur' },
    { min: 2, max: 100, message: 'Length should be 2 to 100', trigger: 'blur' }
  ],
  message: [
    { required: true, message: 'Please enter a message', trigger: 'blur' },
    { min: 2, max: 500, message: 'Length should be 2 to 500', trigger: 'blur' }
  ]
}

const submitForm = async () => {
  isLoading.value = true
  try {
    await formRef.value.validate()
    // Here you would typically send the form data to your backend
    // For now, we'll just show a success message
    ElMessage({
      message: 'Message sent successfully!',
      type: 'success'
    })
    // Reset form
    formRef.value.resetFields()
  } catch (error) {
    console.error('Form validation failed:', error)
  } finally {
    isLoading.value = false
  }
}
</script>

<style scoped>
.contact-info {
  display: flex;
  justify-content: center;
  gap: 1rem;
}

.el-card {
  text-align: center;
}

.el-icon {
  font-size: 2rem;
  margin-bottom: 0.5rem;
}

.el-card__body {
  padding: 2rem;
}
</style>
