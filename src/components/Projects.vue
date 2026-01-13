<template>
	            <section class="pb-5" id="projects">
                    <h1 class="mt-5 mb-5 pb-4 text-center">My Projects</h1>
                <!-- 1st Projects Placeholder-->
                <div
                	v-for = "(group, index) in chunkProjects"
                	:key = "index"
                	class = "card-deck my-5 justify-content-center"
                >
                	<ProjectCard
                		v-for="project in group"
                		:project = "project"
                		:key = "project.id"
                	/>
            	</div>
            </section>
</template>

<script setup>
	// compute 
	import {computed} from "vue";
	import ProjectCard from "./ProjectCard.vue";
	import projects from "../data/projects.json";

	// This will be used to define the number of cards per row.
	const chunkSize = 3;

	// Create a computed property that splits the projects into smaller arrays called chunks.
	// Each chunk will contain up to the number of the chunkSize number of projects.
	// This allows us to group them visually in separate rows in the UI.

	const chunkProjects = computed(()=>{
		const chunk = [];
		for (let i=0; i < projects.length; i+=chunkSize){
			chunk.push(projects.slice(i, i+chunkSize));
		}
		return chunk;
	})
</script>