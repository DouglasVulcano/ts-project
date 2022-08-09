<template>
  <div class="app">
    <header>
      <div class="order">
        <button @click="handleClick('title')">Order by title</button>
        <button @click="handleClick('salary')">Order by salary</button>
        <button @click="handleClick('location')">Order by location</button>
      </div>
    </header>

    <ListComponent :jobs="jobs" :order="order" />
  </div>
</template>

<script lang="ts">
import { defineComponent, ref } from "vue";
import ListComponent from "@/components/ListComponent.vue";
import Job from "src/types/Job";
import OrderTerm from "src/types/OrderTerm";

export default defineComponent({
  name: "IndexPage",
  components: {
    ListComponent,
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
      ]),
      order = ref<OrderTerm>("title");

    const handleClick = (term: OrderTerm) => {
      order.value = term;
    };

    return { jobs, order, handleClick };
  },
});
</script>

<style scoped>
header {
  text-align: center;
}
header .order {
  margin-top: 20px;
}
button {
  margin: 0 10px;
  color: #1195c9;
  border: 3px solid #1195c9;
  background: #d5f0ff;
  padding: 8px 16px;
  border-radius: 4px;
  cursor: pointer;
  font-weight: bold;
}
</style>
