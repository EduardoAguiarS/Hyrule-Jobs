<template>
  <div class="job-list">
    <ul>
      <li v-for="job in jobs" :key="job.id">
        <!-- Title -->
        <h2>{{ job.title }} in {{ job.location }}</h2>
        <!-- Salary -->
        <div class="salary">
          <p>{{ job.salary }} rupees</p>
        </div>
        <!-- Description -->
        <div class="description">
          <p>
            Lorem ipsum dolor sit amet consectetur adipisicing elit. Voluptate hic consequatur aperiam iure mollitia
            ex nostrum quidem inventore. Mollitia quo exercitationem itaque ipsum, unde dolore repudiandae molestiae
            quam consequuntur vero!
          </p>
        </div>
      </li>
    </ul>
  </div>
</template>

<script lang="ts">
import { defineComponent, PropType } from 'vue'
import Job from '@/types/Job'

export default defineComponent({
  props: {
    jobs: {
      type: Array as PropType<Job[]>,
      required: true
    }
  }
})
</script>

<style scoped>
.job-list {
  max-width: 960px;
  margin: 40px auto;
}
.job-list ul {
  list-style: none;
  padding: 0;
}
.job-list li {
  background-color: #fff;
  border-radius: 4px;
  margin: 1rem 0;
  padding: 1rem;
}
.job-list li h2 {
  margin: 0 0 10px;
  text-transform: capitalize;
}
.job-list li .salary {
  display: flex;
}
.job-list li .salary p {
  margin: 10px 4px;
  font-weight: bold;
  color: #17bf66;
}
.job-list li .salary img {
  width: 30px;
}
</style>
