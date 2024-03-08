<template>
  <div id="app">
    <!-- Header Section -->
    <header>
      <div class="header-container">
        <h1>{{ fullName }}</h1>
        <nav>
          <ul>
            <li><a href="#about">About</a></li>
            <li><a href="#portfolio">Portfolio</a></li>
            <li><a href="#skills">Skills</a></li>
            <li><a href="#testimonials">Testimonials</a></li>
            <li><a href="#contact">Contact</a></li>
          </ul>
        </nav>
      </div>
    </header>
    
    <!-- About Section -->
    <section id="about" class="section">
      <div class="container">
        <h2>About Me</h2>
        <div class="about-content">
          <img src="profile-pic.jpg" alt="Profile Picture" class="profile-pic">
          <p>{{ aboutContent }}</p>
        </div>
      </div>
    </section>
    
    <!-- Portfolio Section -->
    <section id="portfolio" class="section">
      <div class="container">
        <h2>Portfolio</h2>
        <div class="projects">
          <div v-for="project in projects" :key="project.id" class="project">
            <h3>{{ project.title }}</h3>
            <p>{{ project.description }}</p>
            <a :href="project.link">View Project</a>
          </div>
        </div>
      </div>
    </section>
    
    <!-- Skills Section -->
    <section id="skills" class="section">
      <div class="container">
        <h2>Skills</h2>
        <div class="skills">
          <div v-for="(skill, index) in skills" :key="index" class="skill">
            <h3>{{ skill.name }}</h3>
            <div class="skill-level" :style="{ width: skill.level + '%' }"></div>
          </div>
        </div>
      </div>
    </section>
    
    <!-- Testimonials Section -->
    <section id="testimonials" class="section">
      <div class="container">
        <h2>Testimonials</h2>
        <div class="testimonials">
          <div v-for="(testimonial, index) in testimonials" :key="index" class="testimonial">
            <p>{{ testimonial.content }}</p>
            <span>- {{ testimonial.author }}</span>
          </div>
        </div>
      </div>
    </section>
    
    <!-- Contact Section -->
    <section id="contact" class="section">
      <div class="container">
        <h2>Contact Me</h2>
        <form @submit.prevent="submitForm" class="contact-form">
          <label for="name">Name:</label>
          <input type="text" id="name" v-model="name" required>
          <label for="email">Email:</label>
          <input type="email" id="email" v-model="email" required>
          <label for="message">Message:</label>
          <textarea id="message" v-model="message" required></textarea>
          <button type="submit">Submit</button>
        </form>
      </div>
    </section>
    
    <!-- Footer Section -->
    <footer>
      <p>&copy; {{ currentYear }} {{ fullName }} - All Rights Reserved</p>
    </footer>
  </div>
</template>

<script>
export default {
  data() {
    return {
      fullName: "Your Name",
      aboutContent: "A brief description about yourself...",
      projects: [
        {
          id: 1,
          title: "Project 1",
          description: "Description of Project 1",
          link: "https://example.com/project1"
        },
        {
          id: 2,
          title: "Project 2",
          description: "Description of Project 2",
          link: "https://example.com/project2"
        },
        // Add more projects as needed
      ],
      skills: [
        { name: "HTML", level: 90 },
        { name: "CSS", level: 85 },
        { name: "JavaScript", level: 80 },
        // Add more skills as needed
      ],
      testimonials: [
        { content: "Testimonial 1 content", author: "Testimonial 1 author" },
        { content: "Testimonial 2 content", author: "Testimonial 2 author" },
        // Add more testimonials as needed
      ],
      name: "",
      email: "",
      message: ""
    };
  },
  computed: {
    currentYear() {
      return new Date().getFullYear();
    }
  },
  methods: {
    submitForm() {
      // Handle form submission (e.g., send data to server)
      console.log("Form submitted!");
    }
  }
};
</script>

<style scoped>
/* Add your CSS styles here */

/* General styles */
body {
  font-family: Arial, sans-serif;
  margin: 0;
  padding: 0;
}

.container {
  max-width: 1200px;
  margin: 0 auto;
  padding: 0 20px;
}

.section {
  padding: 50px 0;
}

/* Header styles */
header {
  background-color: #333;
  color: #fff;
  padding: 20px 0;
  position: fixed;
  width: 100%;
  top: 0;
  left: 0;
  z-index: 1000;
}

.header-container {
  display: flex;
  justify-content: space-between;
  align-items: center;
}

nav ul {
  list-style: none;
  padding: 0;
  margin: 0;
}

nav ul li {
  display: inline;
  margin-right: 20px;
}

nav ul li a {
  color: #fff;
  text-decoration: none;
}

/* Main styles */
main {
  padding-top: 80px; /* Adjust based on header height */
}

/* About Section styles */
.about-content {
  display: flex;
  align-items: center;
}

.profile-pic {
  width: 200px;
  border-radius: 50%;
  margin-right: 20px;
}

/* Portfolio Section styles */
.projects {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
  gap: 20px;
}

.project {
  background-color: #f4f4f4;
  padding: 20px;
  border-radius: 5px;
}

/* Skills Section styles */
.skills {
  display: flex;
  flex-wrap: wrap;
}

.skill {
  flex: 1 1 200px;
  margin: 10px;
}

.skill h3 {
  margin: 0;
}

.skill-level {
  background-color: #007bff; /* Change color based on skill level */
  height: 20px;
  border-radius: 5px;
}

/* Testimonials Section styles */
.testimonials {
  display: flex;
  flex-wrap: wrap;
}

.testimonial {
  flex: 1 1 400px;
  padding: 20px;
  background-color: #f4f4f4;
  border-radius: 5px;
  margin: 10px;
}

/* Contact Section styles */
.contact-form {
  max-width: 400px;
  margin: 0 auto;
}

.contact-form label {
  display: block;
  margin-bottom: 10px;
}

.contact-form input[type="text"],
.contact-form input[type="email"],
.contact-form textarea {
  width: 100%;
  padding: 10px;
  margin-bottom: 20px;
  border: 1px solid #ccc;
  border-radius: 5px;
}

.contact-form button {
  background-color: #333;
  color: #fff;
  padding: 10px 20px;
  border: none;
  border-radius: 5px;
  cursor: pointer;
  transition: background-color 0.3s ease;
}

.contact-form button:hover {
  background-color: #555;
}

/* Footer styles */
footer {
  background-color: #333;
  color: #fff;
  text-align: center;
  padding: 20px 0;
  position: relative;
  bottom: 0;
  width: 100%;
}
</style>
