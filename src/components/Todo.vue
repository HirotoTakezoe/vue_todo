<template>
  <div class="todo">
    {{ msg }}
    <form>
      <button @click="addTodo()">ADD TASK</button>
      <button @click="removeTodo()">DELETE FINISHED TASKS</button>
      <p>input: <input type="text" v-model="newTodo"></p>
      <p>task: {{ newTodo }}</p>
    </form>
    <div class="task-list">
      <label class="task-list__item" v-for="todo in todos">
        <input type="checkbox" v-model="todo.done"><button>EDIT</button>{{ todo.text }}
      </label>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Todo',
  data () {
    return {
      msg: 'Welcome to Your Vue.js App',
      todos: [
        { text: 'vue-router', done: false },
        { text: 'vuex', done: false },
        { text: 'vue-loader', done: false },
        { text: 'awesome-vue', done: true }
      ],
      newTodo: ''
    }
  },
  methods: {
    addTodo (event) {
      // thisでdata()にアクセスできる
      let text = this.newTodo && this.newTodo.trim()
      // 空だった場合は追加しない
      if (!text) {
        return
      }
      // textの値をtodoに追加
      this.todos.push({
        text: text,
        done: false
      })
      // inputの中身初期化
      this.newTodo = ''
    },
    removeTodo (event) {
      // checkされている要素を下から探索して削除していく
      console.log(this.todos.length)
      for (let i = this.todos.length - 1; i >= 0; i--) {
        if (this.todos[i].done) {
          // i番目のtodosを削除
          this.todos.splice(i, 1)
        }
      }
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="scss" scoped>
@mixin flex-vender() {
  display: flex;
  display: -webkit-flex;
  display: -moz-flex;
  display: -ms-flex;
  display: -o-flex;
}
.task-list {
  @include flex-vender;
  flex-direction: column;
  align-items: center;
  &__item {
    width: 270px;
    text-align: left;
    $element: #{&};
    &--checked {
      @extend #{$element};
      color: #85a6c6;
    }
  }
}
</style>
