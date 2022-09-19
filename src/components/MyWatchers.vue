<script>
import axios from 'axios';

export default {
  data() {
    return {
      todoId: 1,
      todoData: null, //초기값을 null로 설정
    };
  },

  methods: {
    async fetchData() {
      this.todoData = null; //초기값을 null
      const res = await axios.get('https://jsonplaceholder.typicode.com/todos/' + this.todoId);
      this.todoData = res.data;
    },
  },

  mounted() {
    this.fetchData();
  },

  watch: {
    todoId(newTodo) {
      console.log(newTodo);
      this.fetchData();
    },
  },
};
</script>
<template>
  <div>
    <p>Todo id..: {{ todoId }}</p>
    <button @click="todoId++">Fetch next</button>
    <p v-if="!todoData">Loading...</p>
    <pre v-else>{{ todoData }}</pre>
  </div>
</template>
