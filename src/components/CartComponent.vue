<template>
  <div class="container mt-5">
    <div class="row justify-content-center text-center">
      <div class="col-md-8">
        <div class="card">
          <div class="card-header" v-if="cartHeader">{{ cartHeader }}</div>
          <div class="card-body">
            <form @submit.prevent="addTodo">
            <div class="input-group">
              <input type="text" class="form-control" placeholder="Add Todo " v-model="todo" />
              <button class="btn btn-primary" type="submit" v-if="!isUpadate">Add</button>
              <button class="btn btn-primary" type="submit" @click="updatedTodo(updateIndex)" v-else>Save</button>
            </div>
        </form>
            <div class="row mt-3" v-if="todos.length>0">
              <table class="table table-bordered table-striped">
                <thead>
                  <tr class="table-primary">
                    <th>Todo</th>
                    <th>Action</th>
                  </tr>
                </thead>
                <tbody>
                  <tr v-for="(todo,index) in todos" :key="index">
                    <td  :class="{'text-danger': todo.status}"><del v-if="todo.status">{{ todo.title }}</del><span v-else>{{ todo.title }}</span></td>
                    <td width="200px">
                      <i class="fas fa-check text-primary mx-2" @click="doneTodo(index)"></i>
                      <i class="fas fa-pencil text-info mx-2" @click="editTodo(index)"></i>
                      <i class="fas fa-trash text-danger mx-2" @click="deleteTodo(todo.id)"></i>
                    </td>
                  </tr>
                </tbody>
              </table>
            </div>
            <div class="row" v-else>
              <p >No Todo found hare...</p>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>
<script>
import { v4 as uuidv4 } from 'uuid';
export default {

  props: ["cartHeader"],
  data() {
    return {
        todo:'',
        isUpadate:false,
        updateIndex:'',
        isCompelete:false,
      todos: []
    };
  },
  methods: {
    addTodo(){
        const data = {
            id:uuidv4(),
            title: this.todo,
            status: this.isCompelete
        }
        this.todos = [...this.todos,data]
        this.todo = ''
    },
    doneTodo(index){
      this.todos[index].status = !this.todos[index].status
    },
    editTodo(index){
        this.isUpadate = !this.isUpadate
        this.todo = this.todos[index].title
        this.updateIndex = index
        
    },
    updatedTodo(index){
      this.todos[index].title = this.todo
    },
    deleteTodo(index){
        this.todos = this.todos.filter(item =>item.id!==index)
    }
  }
};
</script>