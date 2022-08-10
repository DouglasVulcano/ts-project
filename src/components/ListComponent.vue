<template>
  <div class="job-list">
    <ul>
      <li v-for="job in orderedJobs" :key="job.id">
        <h2>{{ job.title }} in {{ job.location }}</h2>
        <div class="salary">
          <p>{{ job.salary }}</p>
        </div>
        <div class="description">
          It has survived not only five centuries, but also the leap into
          electronic typesetting, remaining essentially unchanged. It was
          popularised in the 1960s with the release of Letraset sheets
          containing Lorem Ipsum passages, and more recently with desktop
          publishing software like Aldus PageMaker including versions of Lorem
          Ipsum.
        </div>
      </li>
    </ul>
  </div>
</template>

<script lang="ts">
import { computed, defineComponent, PropType } from "vue";
import Job from "src/types/Job";
import OrderTerm from "src/types/OrderTerm";

export default defineComponent({
  name: "ListComponent",

  props: {
    jobs: {
      type: Array as PropType<Job[]>, // Type as Array<Job> to can use :key on v-for's
      required: true,
    },
    order: {
      type: String as PropType<OrderTerm>,
      required: true,
    },
  },

  setup(props) {
    const orderedJobs = computed(() => {
      return [...props.jobs].sort((a: Job, b: Job) => {
        return a[props.order] > b[props.order] ? 1 : -1;
      });
    });

    return { orderedJobs };
  },
});
</script>

<style scoped>
.job-list {
  max-width: 860px;
  margin: 40px auto;
}
.job-list ul {
  padding: 0;
}
.job-list li {
  list-style-type: none;
  background: white;
  padding: 16px;
  margin: 16px 0;
  border-radius: 4px;
}
.job-list h2 {
  margin: 0 0 10px;
  text-transform: capitalize;
}
.salary {
  display: flex;
}
.salary img {
  width: 30px;
}
.salary p {
  color: #17bf66;
  font-weight: bold;
  margin: 10px 4px;
}
</style>
