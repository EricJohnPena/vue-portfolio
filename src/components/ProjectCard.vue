<template>
    <div class="col-lg-4 col-md-6">
        <div class="card project-card h-100">
            <div class="d-flex align-items-center justify-content-center bg-dark text-white">
                <img :src="project.image" class="img-fluid card-img"  loading="lazy">
            </div>
            <div class="card-body p-4 d-flex flex-column">
                <div class="d-flex justify-content-between align-items-start mb-2">
                    <h5 class="card-title fw-bold mb-0">{{ project.title }}</h5>
                    <span class="badge bg-light text-dark border">API Docs</span>
                </div>
                <p class="card-text text-muted small flex-grow-1">
                   {{ project.description }}
                </p>
                <div class="d-flex justify-content-between align-items-center mt-4">
                    <div class="tech-tags text-muted small">{{ project.tags }}</div>
                    <a 
                        v-if="project.link" 
                        :href="project.link" 
                        target="_blank" 
                        rel="noopener noreferrer" 
                        class="btn btn-sm btn-outline-custom view-link"
                    >
                        View
                    </a>
                </div>
            </div>
        </div>
    </div>

</template>
                        
<script setup>
    import { defineProps } from 'vue';

    defineProps({
        project: Object
    })
</script>