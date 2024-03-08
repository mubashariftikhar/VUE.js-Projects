<template>
  <div id="app">
    <header>
      <div class="header-container">
        <h1>{{ fullName }}</h1>
        <nav>
          <ul>
            <li><a href="#about">About</a></li>
            <li><a href="#portfolio">Portfolio</a></li>
            <li><a href="#contact">Contact</a></li>
          </ul>
        </nav>
      </div>
    </header>
    
    <main>
      <section id="about" class="section">
        <div class="container">
          <h2>About Me</h2>
          <div class="about-content">
            <img src="profile-pic.jpg" alt="Profile Picture" class="profile-pic">
            <p>{{ aboutContent }}</p>
          </div>
        </div>
      </section>
      
      <section id="portfolio" class="section">
        <div class="container">
          <h2>Portfolio</h2>
          <div class="projects">
            <div v-for="project in projects" :key="project.id" class="project">
              <div class="project-content">
                <h3>{{ project.title }}</h3>
                <p>{{ project.description }}</p>
                <a :href="project.link">View Project</a>
              </div>
            </div>
          </div>
        </div>
      </section>
      
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
    </main>
    
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

header {
  background-color: #333;
  color: #fff;
  padding: 20px 0;
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

main {
  padding-top: 80px; /* Adjust based on header height */
}

.about-content {
  display: flex;
  align-items: center;
}

.profile-pic {
  width: 200px;
  border-radius: 50%;
  margin-right: 20px;
}

.projects {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
  gap: 20px;
}

.project {
  background-color: #fff;
  padding: 20px;
  border-radius: 5px;
  box-shadow: 0px 0px 10px rgba(0, 0, 0, 0.1);
  transition: transform 0.3s ease;
}

.project:hover {
  transform: translateY(-5px); /* Add a subtle hover effect */
}

.project h3 {
  margin: 0;
}

.project p {
  margin-bottom: 10px;
}

.project a {
  color: #333;
  text-decoration: none;
  transition: color 0.3s ease;
}

.project a:hover {
  color: #007bff; /* Change color on hover */
}

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

footer {
  background-color: #333;
  color: #fff;
  text-align: center;
  padding: 20px 0;
}
</style>
