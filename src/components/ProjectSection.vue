<script setup>
import ProjectCard from './ProjectCard.vue';
import projects from '../data/projects.json';


</script>

<template>
    <!-- Projects Section Start -->
        <section id="projects" class="projects-section py-5">
            <div class="container py-5">
                <div class="text-center mb-5">
                    <span class="section-badge">PROJECTS</span>
                </div>

                <!-- Projects Grid -->
                <div class="row g-4">
                    <ProjectCard v-for="project in projects" 
                :key="project.id" 
                :project="project" />

                </div>
            </div>
        </section>
    <!-- Projects Section End -->
</template>