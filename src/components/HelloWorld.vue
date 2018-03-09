<template>
  <main role="main" class="container">
    <div class="d-flex align-items-center p-3 my-3 text-white-50 bg-purple rounded box-shadow">
      <img class="mr-3" src="https://getbootstrap.com/assets/brand/bootstrap-outline.svg" alt="" width="48" height="48">
      <div class="lh-100">
        <h6 class="mb-0 text-white lh-100">Todos</h6>
        <small>Since 2011</small>
      </div>
    </div>

    <div class="my-3 p-3 bg-light rounded box-shadow todo-list">
      <!-- v-model="allDone" -->
      <input class="toggle-all" type="checkbox">
      <input autofocus="autofocus" autocomplete="off" placeholder="What needs to be done?" class="new-todo" @keyup.enter="addTodo" v-model="todoItem">

      <li class="media text-muted pt-3 todo" v-on:mouseover="mouseOver" v-for="(item, i) in todos">
        <input type="checkbox" class="toggle">
        <p class="media-body pb-3 mb-0 small lh-125 border-bottom border-gray ml-3">
          <strong class="d-block text-gray-dark">{{ item }}</strong>
        </p>
        <button class="destroy"></button>
      </li>

      <small class="d-block mt-3">
        <span class="todo-count">item left</span>
        <span class="todo-count" v-show="false">items left</span>
        <ul class="filters">
          <li>
            <a href="#/all" class="selected">All</a>
          </li>
          <li>
            <a href="#/active" class="">Active</a>
          </li>
          <li>
            <a href="#/completed" class="">Completed</a>
          </li>
        </ul>
        <a class="ml-3" href="#">Clear completed</a>
      </small>
    </div>
  </main>
</template>

<script>
export default {
  name: 'HelloWorld',
  data() {
    return {
      todos: ['Learn vue.js 2.x', 'Learn vue.js with webpack'],
      todoItem: '',
      active: true
    }
  },
  methods: {
    mouseOver() {
      // console.log("hover")
      // this.active = !this.active;
    },
    addTodo() {
      this.todos.push(this.todoItem)
      // console.log(this.todos)
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style  lang="scss">
@import '~bootstrap/scss/bootstrap';
html,
body {
  overflow-x: hidden; /* Prevent scroll on narrow devices */
}

.container {
  max-width: 800px;
}

.toggle-all {
  border: none;
  -webkit-appearance: none;
  -webkit-transform: rotate(90deg);
  -moz-transform: rotate(90deg);
  -o-transform: rotate(90deg);
  -ms-transform: rotate(90deg);
  transform: rotate(90deg);
}

.toggle-all:before {
  content: '❯';
  font-size: 22px;
  color: #e6e6e6;
  padding: 10px 27px 10px 27px;
}

.toggle-all:checked:before {
  color: #737373;
}

.todo-list li .toggle {
  border: none;
  -webkit-appearance: none;
}

input:focus {
  outline: 0;
}

.todo-list li .toggle:after {
  content: url('data:image/svg+xml;utf8,<svg xmlns="http://www.w3.org/2000/svg" width="40" height="40" viewBox="-10 -18 100 135"><circle cx="50" cy="50" r="50" fill="none" stroke="#ededed" stroke-width="3"/></svg>');
}

.todo-list li .toggle:checked:after {
  content: url('data:image/svg+xml;utf8,<svg xmlns="http://www.w3.org/2000/svg" width="40" height="40" viewBox="-10 -18 100 135"><circle cx="50" cy="50" r="50" fill="none" stroke="#bddad5" stroke-width="3"/><path fill="#5dc2af" d="M72 25L42 71 27 56l-4 4 20 20 34-52z"/></svg>');
}

.todo-list .completed p {
  color: #d9d9d9;
  text-decoration: line-through;
}

.new-todo {
  padding: 16px 16px 16px 16px;
  border: none;
  background: rgba(0, 0, 0, 0.003);
  box-shadow: inset 0 -2px 1px rgba(0, 0, 0, 0.03);
}

button {
  margin: 0;
  padding: 0;
  border: 0;
  background: none;
  font-size: 100%;
  vertical-align: baseline;
  font-family: inherit;
  font-weight: inherit;
  color: inherit;
  -webkit-appearance: none;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}
button:focus {outline:0;}

.todo{
  position: relative;
}

.todo-list li .destroy {
  display: none;
  position: absolute;
  top: 0;
  right: 10px;
  bottom: 10px;
  width: 40px;
  height: 40px;
  margin: auto 0;
  font-size: 30px;
  color: #cc9a9a;
  margin-bottom: 11px;
  transition: color 0.2s ease-out;
}

.todo-list li .destroy:hover {
  color: #af5b5e;
}

.todo-list li .destroy:after {
  content: '×';
}

.todo-list li:hover .destroy {
  display: block;
}

.todo-count {
  float: left;
  text-align: left;
}

.filters {
  display: inline;
  li {
    display: inline;
  }
}

.nav-scroller {
  position: relative;
  z-index: 2;
  height: 2.75rem;
  overflow-y: hidden;
}

.nav-scroller .nav {
  display: -webkit-box;
  display: -ms-flexbox;
  display: flex;
  -ms-flex-wrap: nowrap;
  flex-wrap: nowrap;
  padding-bottom: 1rem;
  margin-top: -1px;
  overflow-x: auto;
  color: rgba(255, 255, 255, 0.75);
  text-align: center;
  white-space: nowrap;
  -webkit-overflow-scrolling: touch;
}

.nav-underline .nav-link {
  padding-top: 0.75rem;
  padding-bottom: 0.75rem;
  font-size: 0.875rem;
  color: var(--secondary);
}

.nav-underline .nav-link:hover {
  color: var(--blue);
}

.nav-underline .active {
  font-weight: 500;
  color: var(--gray-dark);
}

.text-white-50 {
  color: rgba(255, 255, 255, 0.5);
}

.bg-purple {
  background-color: var(--purple);
}

.border-bottom {
  border-bottom: 1px solid #e5e5e5;
}

.box-shadow {
  box-shadow: 0 0.25rem 0.75rem rgba(0, 0, 0, 0.05);
}

.lh-100 {
  line-height: 1;
}
.lh-125 {
  line-height: 1.25;
}
.lh-150 {
  line-height: 1.5;
}
</style>
