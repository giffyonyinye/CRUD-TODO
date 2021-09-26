<template>
  <section>

    <header>
      <h1>MY TODO LIST</h1>
    </header>
    <form @submit.prevent="addTodo()">
      <div>
        <label for="todoTitle">Todo Title</label><br>
        <input type="text" name="name" id="name" v-model="todoName">
      </div>

      <div class="form-control">
           <label for="referral">Status</label>
           <select name="status" id="status" v-model="status">
               <option value="active">Active</option>
               <option value="completed">Completed</option>
           </select>
      </div>

      <button>Add Todo</button>

    </form>

    <div v-for="todo in todos" :key="todo">
      <div style="display:flex; justify-content:space-around">
        <div>
          <p>{{todo.todoName}}</p>
          <p>{{todo.status}}</p>
        </div>

        <div>
          <button @click="removeTodo(id)">X</button>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  data() {
    return {
      todoName: "",
      status: "",
      todos: []
    }
  },

  methods: {
    addTodo() {
      console.log(this.todoName)
      const todo = {
        id: Math.random(),
        todoName:this.todoName,
        status: this.status
      }
      this.todos.push(todo)
      console.log(this.todos)
      
      return (
        this.todoName = "",
        this.status = ""
      )
      
    },

    removeTodo(id) {
     console.log(this.todos.filter(i => i !== id))

    }
  }
}
</script>

<style>
* {
  padding: 0;
  margin: 0;
  box-sizing: border-box;
  font-weight: 100;
}
  header {
    background-color: purple;
    text-align: center;
    color: white;
    padding: 1rem;
    font-size: 1.5rem;
  }
</style>

