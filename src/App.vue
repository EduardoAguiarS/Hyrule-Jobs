<template>
  <header>
    <div class="order">
      <button @click.prevent="handleClick('title')">order by title</button>
      <button @click.prevent="handleClick('salary')">order by salary</button>
      <button @click.prevent="handleClick('location')">order by location</button>
    </div>
  </header>
  <JobsList :jobs='jobs' :order="order" />
</template>

<script lang="ts">
import { defineComponent, ref } from 'vue';
// Components
import JobsList from '@/components/JobsList.vue';
// Types
import Job from '@/types/Job';
import OrderTerm from '@/types/OrderTerm';

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

    const order = ref<OrderTerm>('title');
    const handleClick = (term: OrderTerm) => {
      order.value = term;
    }

    return { jobs, handleClick, order };
  },
});
</script>

<style>
  header {
    text-align: center;
  }
  header .order {
    margin-top: 20px;
  }
  button {
    margin: 0 10px;
    color: #1195c9;
    border: 2px solid #1195c9;
    background: #d5f0ff;
    padding: 8px 16px;
    border-radius: 4px;
    cursor: pointer;
    font-weight: bold;
  }
</style>
