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
      hideCompleted: false,
      todos: [
        { id: id++, text: 'Learn HTML', done: true },
        { id: id++, text: 'Learn JavaScript', done: true },
        { id: id++, text: 'Learn Vue', done: false },
      ],
    };
  },

  computed: {
    filteredTodos() {
      return this.hideCompleted ? this.todos.filter((todo) => !todo.done) : this.todos;
    },
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
      this.todos.push({ id: id++, text: this.newTodo, done: false });
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

    <form @submit.prevent="addTodo">
      <input v-model="newTodo" placeholder="todo" />
      <button>Add Todo</button>
    </form>

    <ul>
      <li v-for="todo in filteredTodos" :key="todo.id">
        <input type="checkbox" v-model="todo.done" />
        <span :class="{ done: todo.done }"> {{ todo.text }}</span>
        <button @click="removeTodo(todo)">X</button>
      </li>
    </ul>

    <button @click="hideCompleted = !hideCompleted">
      {{ hideCompleted ? 'Show all' : 'Hide completed' }}
    </button>
  </div>
</template>

<style>
.red {
  color: red;
}

.blue {
  color: blue;
}

.done {
  text-decoration: line-through;
}
</style>
