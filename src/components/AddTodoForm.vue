<template>
<div>
    <h1>{{ formTitle }}{{title}}</h1>
    <div><br/><button v-on:click="showForm()" style="background:blue; color:white;">Add New Task</button></div>
    <div>
        <div v-show="isEditing">
            <h2>Adding a task</h2>

                    <div>
                        Task title:
                    </div>
                    <div>
                        <input type="text" name="title" v-model="taskTitle" />
                    </div>

                    <div>
                        Task name:
                    </div>
                    <div>
                        <input type="tex" name="taskname" v-model="taskName" />
                    </div>

                    <div>
                        <button v-on:click="closeForm()" >close</button>&nbsp;&nbsp;&nbsp;
                        <button v-on:click="sendForm()" type="button">submit</button>
                    </div>

        </div>
    </div>
</div>

</template>

<script>
    export default {
        props:[
            "title"
        ],

        data(){
            return{
                formTitle:"Add New Task",
                count: 0,
                secondname :"",
                taskTitle:"",
                taskName:"",
                date: Date(),
                isEditing: false,
                todos:[]

            }
        },
        methods:{
            showForm(){
                this.isEditing = true;
            },
            closeForm(){
                this.isEditing = false;
            },
            sendForm (){
                let id = this.todos.length +1;

                if(this.taskTitle!='' && this.taskName!='') {
                    const date = new Date();
                    const done = false;

                    let newTodos = {id:id,title:this.taskTitle,Task:this.taskName,date:this.date,done:this.done};
                    this.todos.push(newTodos);
                    this.newTodos = [];
                    console.log(newTodos);
                    this.$emit("taskAdded",newTodos);
                    console.log(this.$root.$emit("taskAdded",newTodos));
                }else{
                    console.log(newTodos);
                }

            },
        }

    }

</script>

<style>
    table{
        align:center;
    }
</style>