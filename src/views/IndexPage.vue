<template>
    <list-component :jobs="jobs" />
</template>

<script lang="ts">
import { defineComponent, ref } from 'vue';
import ListComponent from '@/components/ListComponent.vue';
import Job from 'src/types/Job';

export default defineComponent({
  name: "IndexPage",
  components:{
    ListComponent
  },
  setup() {
    const jobs = ref<Job[]>([
      {
        id: 1,
        title: "Developer",
        description:
          "Lorem ipsum dolor sit amet consectetur adipisicing elit. Quisquam, quidem.",
        company: "Google",
        location: "New York",
        salary: "$100,000",
      },
      {
        id: 1,
        title: "Developer Senior",
        description:
          "Lorem ipsum dolor sit amet consectetur adipisicing elit. Quisquam, quidem.",
        company: "Facebook",
        location: "Manhattan",
        salary: "$150,000",
      },
    ]);
    return { jobs };
  },
});
</script>
