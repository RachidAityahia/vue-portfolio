<template>
  <footer class="footer">
    <div class="footer-content">
      <div class="footer-section">
        <h3>Contact Me</h3>
        <ul class="contact-list">
          <li><a href="mailto:your.email@example.com" class="contact-link"><el-icon><Message /></el-icon> your.email@example.com</a></li>
          <li><a href="tel:+1234567890" class="contact-link"><el-icon><Phone /></el-icon> +1 234 567 890</a></li>
          <li><a href="#" class="contact-link"><el-icon><Location /></el-icon> 123 Portfolio Street</a></li>
        </ul>
      </div>
      <div class="footer-section">
        <h3>Quick Links</h3>
        <ul class="quick-links">
          <li><router-link to="/" class="link">Home</router-link></li>
          <li><router-link to="/about" class="link">About</router-link></li>
          <li><router-link to="/projects" class="link">Projects</router-link></li>
          <li><router-link to="/contact" class="link">Contact</router-link></li>
        </ul>
      </div>
      <div class="footer-section">
        <h3>Connect With Me</h3>
        <div class="social-links">
          <a href="https://github.com/yourusername" class="social-link" target="_blank">
            <el-icon><Link /></el-icon>
          </a>
          <a href="https://linkedin.com/in/yourusername" class="social-link" target="_blank">
            <el-icon><Link /></el-icon>
          </a>
          <a href="https://twitter.com/yourusername" class="social-link" target="_blank">
            <el-icon><Link /></el-icon>
          </a>
        </div>
      </div>
    </div>
    <div class="footer-bottom">
      <p>&copy; {{ currentYear }} Your Name. All rights reserved.</p>
    </div>
  </footer>
</template>

<script setup>
import { ref } from 'vue'
import { Link, Message, Phone, Location } from '@element-plus/icons-vue'

const currentYear = ref(new Date().getFullYear())
</script>

<style scoped>
.footer {
  background-color: #2c3e50;
  color: #ffffff;
  padding: 4rem 2rem 2rem;
  margin-top: auto;
}

.footer-content {
  max-width: 1200px;
  margin: 0 auto;
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
  gap: 2rem;
}

.footer-section h3 {
  margin-bottom: 1.5rem;
  font-size: 1.2rem;
}

.contact-list, .quick-links {
  list-style: none;
  padding: 0;
}

.contact-list li, .quick-links li {
  margin-bottom: 0.75rem;
}

.contact-link, .link {
  color: #ffffff;
  text-decoration: none;
  transition: color 0.3s ease;
  display: flex;
  align-items: center;
  gap: 0.5rem;
}

.contact-link:hover, .link:hover {
  color: #3498db;
}

.social-links {
  display: flex;
  gap: 1rem;
}

.social-link {
  color: #ffffff;
  text-decoration: none;
  font-size: 1.5rem;
  transition: color 0.3s ease;
}

.social-link:hover {
  color: #3498db;
}

.footer-bottom {
  text-align: center;
  margin-top: 3rem;
  padding-top: 2rem;
  border-top: 1px solid rgba(255, 255, 255, 0.1);
}

@media (max-width: 768px) {
  .footer-content {
    grid-template-columns: 1fr;
    text-align: center;
  }
  
  .footer-section {
    margin-bottom: 2rem;
  }
}
</style>
