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
              <button class="btn btn-primary" type="submit">Add</button>
            </div>
        </form>
            <div class="row mt-3">
              <table class="table table-bordered table-striped">
                <thead>
                  <tr class="table-primary">
                    <th>sl</th>
                    <th>Todo</th>
                    <th>Action</th>
                  </tr>
                </thead>
                <tbody>
                  <tr v-for="todo,index in todos" :key="index">
                    <td>{{ ++index }}</td>
                    <td>{{ todo.title }}</td>
                    <td>
                      <button class="btn btn-info mx-2">Edit</button>
                      <button class="btn btn-danger">Delete</button>
                    </td>
                  </tr>
                </tbody>
              </table>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>
<script>
export default {
  props: ["cartHeader"],
  data() {
    return {
        todo:'',
      todos: []
    };
  },
  methods: {
    addTodo(){
        const todo = {
            id:1,
            title: this.todo,
            status: false
        }
        this.todos = [...this.todos,todo]
        this.todo = ''
        console.log(this.todos);
    }
  }
};
</script>
