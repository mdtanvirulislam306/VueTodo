<template>
  <div class="container mt-5">
    <div class="row justify-content-center text-center">
      <div class="col-md-8">
        <div class="card">
          <div class="card-header" v-if="cartHeader">{{ cartHeader }}</div>
          <div class="card-body">
            <form @submit.prevent="addTodo">
<<<<<<< Updated upstream
              <div class="input-group">
                <input
                  type="text"
                  class="form-control"
                  placeholder="Add Todo "
                  v-model="todo"
                />
                <button class="btn btn-primary" type="submit">
                  Add
                </button>
              </div>
            </form>
            <div class="row mt-3" v-if="todos.length > 0">
=======
            <div class="input-group">
              <input type="text" class="form-control" placeholder="Add Todo " v-model="todo" />
              <button class="btn btn-primary" type="submit">Add</button>
            </div>
        </form>
            <div class="row mt-3"  v-if="todos.length>0">
>>>>>>> Stashed changes
              <table class="table table-bordered table-striped">
                <thead>
                  <tr class="table-primary">
                    <th>Todo</th>
                    <th>Action</th>
                  </tr>
                </thead>
                <tbody>
<<<<<<< Updated upstream
                  <tr v-for="(todo, index) in todos" :key="index">
                    <td :class="{ 'text-danger': todo.status }">
                      <del v-if="todo.status">
                        {{ todo.title }}
                      </del>
                      <span v-else>
                        {{ todo.title }}
                      </span>
                    </td>
                    <td width="200px">
                      <i
                        class="fas fa-check text-primary mx-2"
                        @click="doneTodo(index)"
                      ></i>
                      <i
                        class="fas fa-trash text-danger mx-2"
                        @click="deleteTodo(todo.id)"
                      ></i>
=======
                  <tr v-for="(todo,index) in todos" :key="index">
                    <td>{{ ++index }}</td>
                    <td>{{ todo.title }}</td>
                    <td>
                      <button class="btn btn-info mx-2" @click="editTodo(index)">Edit</button>
                      <button class="btn btn-danger" @click="deleteTodo(todo.id)">Delete</button>
>>>>>>> Stashed changes
                    </td>
                  </tr>
                </tbody>
              </table>
            </div>
<<<<<<< Updated upstream
            <div class="row" v-else>
              <p>No Todo found hare...</p>
=======
            <div class="row text-center mt-3" v-else>
              <p>No Todos found...</p>
>>>>>>> Stashed changes
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>
<script>
import { v4 as uuidv4 } from "uuid";
export default {
  props: ["cartHeader"],
  data() {
    return {
      todo: "",
      isCompelete: false,
      todos: [],
    };
  },
  methods: {
    addTodo(){
    
        const data = {
            id:uuidv4(),
            title: this.todo,
            status: false
        }
        this.todos = [...this.todos,data]
        this.todo = ''
    },
    deleteTodo(id){
        this.todos = this.todos.filter(item =>item.id!==id)
    }
  }
};
</script>
