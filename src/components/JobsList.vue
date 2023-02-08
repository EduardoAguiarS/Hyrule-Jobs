<template>
  <div class="job-list">
    <p class="ordered">Ordered by: <span>{{ order }}</span></p>
    <ul>
      <li v-for="job in orderedJobs" :key="job.id">
        <!-- Title -->
        <header>
          <h2>{{ job.title }}</h2>
          <p class="location">
            <img src="https://objmap.zeldamods.org/icons/mapicon_dungeon.svg" alt="location">
            {{ job.location }}
          </p>
        </header>
        <!-- Salary -->
        <div class="salary">
          <img src="../assets/rupee.png" alt="rupee">
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
import { computed, defineComponent, PropType } from 'vue'
// Types
import Job from '@/types/Job'
import OrderTerm from '@/types/OrderTerm';

export default defineComponent({
  props: {
    jobs: {
      type: Array as PropType<Job[]>,
      required: true
    },
    order: {
      type: String as PropType<OrderTerm>,
      required: true
    }
  },
  setup(props) {
    const orderedJobs = computed(() => {
      return [...props.jobs].sort((a: Job, b: Job) => {
        return a[props.order] > b[props.order] ? 1 : -1
      })
    })

    return { orderedJobs }
  }
})
</script>

<style scoped>
.ordered {
  color: #f7f3d762;
  font-size: 0.9rem;
  font-weight: bold;
}
.ordered span {
  color: #f7f3d7;
  text-transform: capitalize;
}
.job-list {
  max-width: 960px;
  margin: 40px auto;
}
.location {
  color: #f7f3d762;
  font-size: 0.9rem;
  font-weight: bold;
  display: flex;
  align-items: center;
  gap: 0.5rem;
  text-transform: capitalize;
}
.job-list ul {
  list-style: none;
  padding: 0;
  height: 500px;
  overflow-y: scroll;
  display: flex;
  flex-direction: column;
  gap: 1rem;
}
.job-list ul::-webkit-scrollbar {
  width: 10px;
}
.job-list ul::-webkit-scrollbar-track {
  background: #12375800;
}
.job-list ul::-webkit-scrollbar-thumb {
  background: #17bf66;
  border-radius: 10px;
}
.job-list li {
  background-color: #123758;
  border-radius: 4px;
  padding: 1rem;
  color: #ebe9d9;
}
.job-list li header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  text-transform: capitalize;
}
.job-list li header h2 {
  font-size: 1.2rem;
  font-weight: bold;
  margin: 0;
  color: #CD9A3c;
}
.job-list li header .location {
  color: #2E93CC;
  font-size: 0.9rem;
  font-weight: bold;
  display: flex;
  align-items: center;
  gap: 0.5rem;
}
.job-list li header .location img {
  width: 40px;
  margin: 0;
}

.job-list li .salary {
  display: flex;
  align-items: center;
  gap: 1rem;
}
.job-list li .salary p {
  margin: 10px 4px;
  font-weight: bold;
  color: #17bf66;
}
.job-list li .salary img {
  width: 20px;
}
.job-list li .description {
  font-size: 0.9rem;
}
</style>
