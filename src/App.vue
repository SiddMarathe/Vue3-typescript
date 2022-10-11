<template>
  <div class="app grid-container">
    <div class="title grid-item1">
      <img src="./assets/love.png"
           alt=""
           class="image">
      <h1>Hyrule Jobs</h1>
    </div>
    <div class="order grid-item2">
      <button @click="handleClick('title')">Order by title</button>
      <button @click="handleClick('salary')">Order by salary</button>
      <button @click="handleClick('location')">Order by location</button>
    </div>
    <div grid-item3>
      <JobList :jobs="jobs"
               :order="order" />
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent, ref } from 'vue';
import Job from "./types/job";
import OrderTerm from "./types/OrderTerm";
import JobList from "./components/JobsList.vue";

export default defineComponent({
  name: 'App',
  components: { JobList },
  setup() {

    // const state = reactive({
    //   name: 'Link',
    //   age: 25 as number | string
    // });

    // return { ...toRefs(state) };
    // const name = ref('Link');
    // const age = ref<number | string>('15');
    // return { name, age };

    const jobs = ref<Job[]>([
      { title: 'farmer', location: 'at the farm', salary: 50000, id: '1' },
      { title: 'quarryman', location: 'death mountain', salary: 20000, id: '2' },
      { title: 'flute player', location: 'high valley', salary: 30000, id: '3' },
      { title: 'fisherman', location: 'high ground', salary: 40000, id: '4' },
      { title: 'dev', location: 'low lane', salary: 10000, id: '5' },
      { title: 'lohar', location: 'gerudo valley', salary: 60000, id: '6' }
    ]);
    const order = ref<OrderTerm>('title');
    const handleClick = (term: OrderTerm) => {
      order.value = term;

    };
    return { order, jobs, handleClick };
  },
  data() {
    return {

    };
  },
  methods: {

  }
});
</script>

<style>
.grid-container {
  display: grid;
  grid-template-columns: auto;
  gap: 10px;
  background-color: darkcyan;
  padding: 10px;
}

.grid-item1 {
  grid-row: 1;
  display: flex;
  justify-content: center;

}

.image {
  width: 50px;
  height: 50px;
  margin-top: 20px;
  margin-right: 4px;
}



.grid-item2 {
  padding-top: 10px;
  grid-row: 2;
  display: flex;
  justify-content: center;
}

.grid-item3 {
  grid-row: 3;
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
