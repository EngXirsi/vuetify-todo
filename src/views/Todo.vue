<template>
<div class="home">
  <v-text-field
    class="pt-3 "
            outlined
            clearable
            v-model= "newTask"
            label="Append"
            append-icon="mdi-plus-circle"
            @click:append = "addTask"
            @keyup.enter="addTask"
        ></v-text-field>
      

    <v-list
    class="pt-0"
      flat
    >
    

  <div  v-for="task in tasks" :key="task.id">
        <v-list-item
          @click = "doneTask(task.id)"
          :class = "{ 'blue lighten-5' : task.done }"
         
        >
        
          <template >
            <v-list-item-action>
              <v-checkbox
                :input-value="task.done"
                color="primary"
              ></v-checkbox>
            </v-list-item-action>

            <v-list-item-content>
              <v-list-item-title
               :class = "{ 'text-decoration-line-through' : task.done }"
              >
                {{task.title}}
                
                
                </v-list-item-title>
             
            </v-list-item-content>
                <v-list-item-action>
          <v-btn icon
           @click.stop= "deleteTask(task.id)"
          >
           
            <v-icon color="red lighten-1">mdi-delete</v-icon>
          </v-btn>
        </v-list-item-action>
          </template>
        </v-list-item>
        <v-divider></v-divider>

  </div>
    </v-list>
    </div>
</template>

<script>
 

  export default {
    name: 'Home',
    data(){
      return {
        newTask : 'nnnn',
        tasks :[
          {
            id :  1,
            title: 'Wake Up',
            done: false
          }, 
          
          {
            id :  2,
            title: 'Get Bananna',
            done: false
          },
             {
            id :  3,
            title: 'Eat Bananna',
            done: true
          },

          ]
      }
    },
    components: {
  
    },
    methods: {
      doneTask(id){
      let task = this.tasks.filter(task => task.id == id)[0];
        console.log(task)
        task.done = !task.done;

      },
      deleteTask(id){
      this.tasks = this.tasks.filter(task => task.id != id);
      },
      addTask(){
      let theNewTask = {
        id : 4,
        title: this.newTask,
        done: false
      };
      this.tasks.push(theNewTask)
      }
    }
  }
</script>
