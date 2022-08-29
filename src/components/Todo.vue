<template>
  <div class="container" style="600px">
    <!-- Create task form -->
    <div class="creatNewTask">
      <div class="d-flex mt-5">

      <span>
    
        <input type='text' class="inputTask py-3" v-model="newTask" placeholder="What are you gonna do"/>

        <button class="btn btn-primary mx-2" data-bs-target="#collapseTarget" data-bs-toggle="collapse" type="submit" v-on:click="onCreateNewTask">
          Create new task
        </button>
        
      </span>
      </div>
    </div>


    <!-- Task table -->
    <div class="taskTable">
      <table>
        <tr v-for="task in tasks" v-bind:key="task.id">
          <td>
            <input type="checkbox" v-model="task.done">
          </td>
          <td>
            <p :style="task.done && { textDecoration: 'line-through' }">{{ task.name }}</p>
          </td>
          <td>
            <button type="button" class="btn btn-danger" v-on:click="() => onDeleteTask(task.id)">Delete</button>
          </td>
        </tr>
      </table>
    </div>
  
  </div>

</template>
  
  <script>
export default {
  name: 'App',
  data() {
    return {
      newTask: '',
      tasks: [],
    };
  },
  methods: {
    onCreateNewTask() {
      this.tasks = [
        {
          id: new Date().getTime(),
          name: this.newTask,
          done: false,
        },
        ...this.tasks,
      ];
      this.newTask = '';
    },
    onDeleteTask(id) {
      this.tasks = this.tasks.filter((task) => task.id !== id);
    },

  },
};
</script>
  
  <style>
  .d-flex{
    display: flex;
    justify-content: center;
    align-items: center;
    text-align: center;
  }
  #app {
    text-align: center;
  }
  
  .creatNewTask {
    margin-bottom: 10px;
  }
  
  .creatNewTask .inputTask {
    width: 300px;
    height: 28px;
  }
  
  .creatNewTask .buttonAdd {
    height: 28px;
    margin-left: 10px;
  }
  
  .taskTable table {
    background-color: aliceblue;
    margin: 0px auto;
    width: 420px;
  }
  
  .taskTable p {
    text-align: left;
  }
  </style>