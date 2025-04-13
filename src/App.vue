<template>
  <div class="min-h-screen bg-green-50 text-white">
    <!-- Header -->
    <header class="bg-emerald-900 py-6 px-8">
      <div class="container mx-auto flex justify-between items-center">
        <h1 class="text-xl font-bold">Beatrice A. Apea-Bah</h1>
        <nav class="hidden md:flex space-x-4">
          <a href="#home" class="hover:text-emerald-600">Home</a>
          <a href="#projects" class="hover:text-emerald-600">Projects</a>
          <a href="#skills" class="hover:text-emerald-600">Skills</a>
          <a href="#contact" class="hover:text-emerald-600">Contact</a>
        </nav>
        <button @click="toggleMenu" class="md:hidden text-white">
          ☰ Menu
        </button>
      </div>
      <div v-if="isMenuOpen" class="md:hidden mt-4 space-y-2">
        <a href="#home" class="block hover:text-emerald-600">Home</a>
        <a href="#projects" class="block hover:text-emerald-600">Projects</a>
        <a href="#skills" class="block hover:text-emerald-600">Skills</a>
        <a href="#contact" class="block hover:text-emerald-600">Contact</a>
      </div>
    </header>

    <!-- Hero Section -->
    <section id="home" class="py-20 text-center">
      <div class="container mx-auto px-6">
        <h1 class="text-4xl text-lime-950 font-bold mb-4">👋 Hi, I'm Beatrice Apea-Bah</h1>
        <p class="text-lg text-lime-950 mb-8 mt-3">Freelance Web Developer | Building Beautiful Websites Is My Thing!😉</p>
        <button class="bg-emerald-900 text-white px-6 py-2 rounded hover:bg-emerald-600 mt-4">
          View My Work
        </button>
      </div>
    </section>

    <!-- Projects Section -->
    <section id="projects" class="py-7">
      <div class="container mx-auto px-6">
        <h2 class="text-5xl text-lime-950 font-bold text-center mb-12">My Projects</h2>
        <div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-3 gap-8">
          <div
            v-for="project in projects"
            :key="project.title"
            class="bg-emerald-900 p-8 rounded-lg shadow-md text-center"
          >
            <h3 class="text-xl font-bold mb-4">{{ project.title }}</h3>
            <p class="text-sm text-white mb-6">{{ project.description }}</p>
            <div class="flex flex-wrap justify-center gap-2 mb-4">
              <span
                v-for="tech in project.tech"
                :key="tech"
                class="bg-emerald-700 px-2 py-1 rounded text-xs text-white"
              >
                {{ tech }}
              </span>
            </div>
            <a :href="project.link" class="text-white hover:underline">View Project</a>
          </div>
        </div>
      </div>
    </section>

    <!-- Skills Section -->
    <section id="skills" class="py-20">
      <div class="container mx-auto px-9">
        <h2 class="text-5xl font-bold text-center mb-16 text-lime-950">My Skills</h2>
        <div class="grid grid-cols-2 sm:grid-cols-3 md:grid-cols-4 lg:grid-cols-5 gap-9">
          <div
            v-for="skill in skills"
            :key="skill.name"
            class="flex items-center space-x-2 text-emerald-950"
          >
            <!-- Skill Icon -->
            <img :src="skill.icon" alt="icon" class="h-9 w-9" />
            <!-- Skill Name -->
            <span>{{ skill.name }}</span>
          </div>
        </div>
      </div>
   </section>

    <!-- Testimonials Section -->
    <section id="testimonials" class="py-20">
      <div class="container mx-auto px-6">
        <h2 class="text-3xl font-bold text-center mb-12 text-lime-950">What Clients Say</h2>
        <div class="grid grid-cols-1 md:grid-cols-2 gap-8">
          <div v-for="testimonial in testimonials" :key="testimonial.name" class="bg-emerald-700 p-6 rounded-lg shadow-md">
            <p class="mb-4">"{{ testimonial.quote }}"</p>
            <p class="font-bold">{{ testimonial.name }}</p>
          </div>
        </div>
      </div>
    </section>

    <!-- Contact Form -->
    <section id="contact" class="py-20">
      <div class="container mx-auto px-6">
        <h2 class="text-3xl font-bold text-center mb-12 text-emerald-950">Get in Touch</h2>
        <form class="max-w-lg mx-auto space-y-4">
          <div>
            <label class="block text-emerald-900 mb-2" for="name">Name</label>
            <input
              type="text"
              id="name"
              placeholder="Your Name"
              class="w-full px-4 py-2 bg-slate-300 text-white border rounded focus:outline-none focus:ring-2 focus:ring-blue-300"
            />
          </div>
          <div>
            <label class="block text-emerald-900 mb-2" for="email">Email</label>
            <input
              type="email"
              id="email"
              placeholder="Your Email"
              class="w-full px-4 py-2 bg-slate-300 text-white border rounded focus:outline-none focus:ring-2 focus:ring-blue-300"
            />
          </div>
          <div>
            <label class="block text-emerald-900 mb-2" for="message">Message</label>
            <textarea
              id="message"
              rows="4"
              placeholder="Your Message"
              class="w-full px-4 py-2 bg-slate-300 text-white border rounded focus:outline-none focus:ring-2 focus:ring-blue-300"
            ></textarea>
          </div>
          <button type="submit" class="bg-emerald-900 text-white px-6 py-2 rounded hover:bg-emerald-600">
            Send Message
          </button>
        </form>
      </div>
    </section>

    <!-- Footer -->
    <footer class="bg-emerald-900 py-4 px-4">
      <div class="container mx-auto text-center">
        <p>&copy; 2023 Beatrice A. Apea-Bah. All rights reserved.</p>
        <div class="flex justify-center space-x-4 mt-4">
          <a href="https://www.linkedin.com/in/beatrice-apea-bah-1a5756312" class="hover:text-emerald-600">LinkedIn</a>
          <a href="https://github.com/BILLIONAIRE-SAGE" class="hover:text-emerald-600">GitHub</a>
          <a href="www.youtube.com/@MmcfraNkcsoc_Academy" class="hover:text-emerald-600">YouTube</a>
        </div>
      </div>
    </footer>
  </div>
</template>

<script setup>
import { ref } from 'vue';

// Mobile menu toggle
const isMenuOpen = ref(false);
const toggleMenu = () => {
  isMenuOpen.value = !isMenuOpen.value;
};

// Sample data
const projects = [
  {
    title: 'Project 1',
    description: 'TrinVoice, the offical website of Trinity Software Company. I was tasked with replicating the site.',
    tech: ['HTML', 'CSS', 'JavaScript'],
    link: 'https://github.com/BILLIONAIRE-SAGE/trinvoice',
  },
  {
    title: 'Project 2',
    description: 'This is a cryptocurrency dashboard i built that allows you to view the stock market in real time.',
    tech: ['Vue.js', 'JavaScript','TailwindCSS'],
    link: 'https://github.com/BILLIONAIRE-SAGE/my-crypto-dashboard',
  },
  {
    title: 'Project 3',
    description: 'This is a quiz app i created during my internship at the Innovation Lab in KNUST.',
    tech: ['HTML', 'CSS', 'JavaScript'],
    link: 'https://github.com/BILLIONAIRE-SAGE/my-crypto-dashboard',
  },
];

const skills = [
  { name: 'HTML', icon: '/assets/html5-brands.svg' },
  { name: 'CSS', icon: '/assets/css-brands.svg' },
  { name: 'JavaScript', icon: '/assets/js-brands.svg' },
  { name: 'Vue.js', icon: '/assets/vuejs-brands.svg' },
  { name: 'TailwindCSS', icon: '/assets/tailwindcss.png' },
  { name: 'Git', icon: '/assets/git-alt-brands.svg' },
  { name: 'Project Management', icon: '/assets/diagram-project-solid.svg' },
  { name: 'Virtual Assistant', icon: '/assets/headphones-solid.svg' },
];

const testimonials = [
  {
    name: 'Salem Hassein',
    quote: 'Great work! Highly recommend this freelancer, She did justice to our Airbnb clone.',
  },
  {
    name: 'Nana Kwame Opoku-Ababio',
    quote: 'Professional and easy to work with.',
  },
  {
    name: 'Veronica Attianeere',
    quote: 'Great team player, hardworking and very ambitious.',
  },
];
</script>