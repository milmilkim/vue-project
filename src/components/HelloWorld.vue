<script>
let id = 0;

export default {
  data() {
    return {
      titleClass: 'blue',
      count: 0,
      text: 'text',
      text2: 'text2',
      awesome: true,

      newTodo: '',
      todos: [
        { id: id++, text: 'Learn HTML' },
        { id: id++, text: 'Learn JavaScript' },
        { id: id++, text: 'Learn Vue' },
      ],
    };
  },

  methods: {
    handleClick() {
      this.count++;
    },

    onInput(e) {
      //v-on handler 인자(e)로 DOM event를 받을 수 있다
      this.text = e.target.value;
    },

    toggle() {
      this.awesome = !this.awesome;
    },

    addTodo() {
      this.todos.push({ id: id++, text: this.newTodo });
      this.newTodo = '';
    },

    removeTodo(task) {
      this.todos = this.todos.filter((todo) => todo.id !== task.id);
    },
  },
};
</script>

<template>
  <div>
    <h1 :class="titleClass">Make me red</h1>
    <button @click="handleClick">count is: {{ count }}</button>
    <button @click="() => this.count++">count is: {{ count }}</button>

    <input :value="text" @input="onInput" placeholder="Type here" />
    <p>{{ text }}</p>

    <input v-model="text2" placeholder="Type here" />
    <p>{{ text2 }}</p>

    <hr />

    <button @click="toggle">toggle</button>

    <h1 v-if="awesome">Vue is awesome!</h1>
    <h1 v-else>Oh, no...</h1>

    <ul>
      <li v-for="todo in todos" :key="todo.id">{{ todo.id }} + {{ todo.text }}</li>
    </ul>

    //양방향 바인딩
    <form @submit.prevent="addTodo">
      <input v-model="newTodo" placeholder="todo" />
      <button>Add Todo</button>
    </form>
    <ul>
      <li v-for="todo in todos" :key="todo.id">
        {{ todo.text }}
        <button @click="removeTodo(todo)">X</button>
      </li>
    </ul>
  </div>
</template>

<style>
.red {
  color: red;
}

.blue {
  color: blue;
}
</style>
