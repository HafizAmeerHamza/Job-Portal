<script setup>
import jobsData from '@/jobs.json';
import { ref, defineProps } from 'vue';
import JobListing from './JobListing.vue';
import { RouterLink } from 'vue-router';

defineProps({
    limit: Number,
    showButton: {
        type: Boolean,
        default: false
    },
    showFilter: {
        type: Boolean,
        default: false
    }
});

const jobs = ref(jobsData);

</script>

<template>

    <section v-if="showFilter" class="bg-green-50 py-4">
      <div class="container mx-auto px-4">
        <div class="relative">
          <input
            type="text"
            class="w-full p-3 border border-gray-300 rounded-lg focus:outline-none focus:border-green-500"
            placeholder="Filter jobs..."
          />
        </div>
      </div>
    </section>

    <section class="bg-green-50 px-4 py-10">
        <div class="container-xl lg:container m-auto">
            <h2 class="text-3xl font-bold text-green-500 mb-6 text-center">
                Browse Jobs
            </h2>
            <div class="grid grid-cols-1 md:grid-cols-3 gap-6">
                <JobListing v-for="job in jobs.slice(0, limit || jobs.length)" :key="job.id" :job="job" />
            </div>
        </div>
    </section>
    <section v-if="showButton" class="m-auto max-w-lg my-10 px-6">
      <RouterLink
        to="/jobs"
        class="block bg-black text-white text-center py-4 px-6 rounded-xl hover:bg-gray-700">
        View All Jobs
        </RouterLink
      >
    </section>
</template>