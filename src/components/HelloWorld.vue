<template>
<div class="container ws">
  <h2>To-Do App</h2>
  <div class="d-flex">
  <div class="input-group mb-3">
    <input type="text" v-model="inputActivities" class="form-control" placeholder="Activities" aria-label="Username" aria-describedby="basic-addon1">
  </div>
  <button @click="submit" class="btn btn-warning rounded-0 tombol">Add</button>
  </div>

  <table class="table">
  <thead>
    <tr>
      <th scope="col">No</th>
      <th scope="col">Activities</th>
      <th scope="col">Progress</th>
      <th scope="col">Action</th>
    </tr>
  </thead>
  <tbody>
    <tr v-for="(item,index) in task" :key="index+1">
      <th scope="row">{{index+1}}</th>
      <td>{{item.name}}</td>
      <td>{{item.status}}</td>
      <td>
        <div @click="deleteTask(item.id)" >
          Delete
          </div> 
      </td>
    </tr>
  </tbody>
</table>


</div>
</template>

<script>
export default {
  name: 'To-Do-App',
  props: {
    msg: String
  },
  data(){
    return{
      inputActivities : '',
      task : [
        {
          id:1,
          name : 'playing tennis',
          status : 'on-progress'
        },
        {
          id:2,
          name : 'Eating Banana',
          status : 'to-do'
        },
      ]
    }
  },
  methods :{
    submit(){
      this.task.push({
        id:this.task.length+1,
        name:this.inputActivities,
        status: 'to-do'
      })
    },
    deleteTask(index){
      console.log(index)
      let newIndex = index
      let result =this.task.filter(item=>item.id !== newIndex)
      // console.log(result)
      this.task= [...result]

    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

.ws{
  background-color: #42b983;
  width: 600px;
  height: 400px;
}

.tombol{
  height: 40px;
}
</style>
