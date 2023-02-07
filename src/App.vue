<template>
  <JobsList :jobs='jobs' />
</template>

<script lang="ts">
import { defineComponent, ref } from 'vue';
import JobsList from '@/components/JobsList.vue';
import Job from '@/types/Job';

export default defineComponent({
  name: 'App',
  components: { JobsList },
  setup() {
    const jobs = ref<Job[]>([
      {
        title: 'farm worker',
        location: 'lon lon ranch',
        salary: 3000,
        id: '1'
      },
      {
        title: 'quarryman',
        location: 'death mountain',
        salary: 4000,
        id: '2'
      },
      {
        title: 'flute player',
        location: 'the lost woods',
        salary: 3500,
        id: '3'
      },
      {
        title: 'fisherman',
        location: 'lake hylia',
        salary: 2000,
        id: '4'
      },
      {
        title: 'prison guard',
        location: 'gerudo valley',
        salary: 5000,
        id: '5'
      }
    ])

    return { jobs }
  },
});
</script>

<style>

</style>
