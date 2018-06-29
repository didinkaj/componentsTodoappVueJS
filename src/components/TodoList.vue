<template>
    <div>
        <h1>{{title}}</h1>
        <div>
            <h2 style="">{{ apptitle }}</h2>

            <div v-on:delete-task="deleteTask" v-for="todo in todos" :key="todo.id">
                <div>{{ todo.title }} &nbsp;&nbsp;&nbsp;{{todo.Task}} &nbsp;&nbsp;&nbsp;<button v-on:click="deleteTask(todo)" >X</button></div>

            </div>
            <todo-form :title="title" ></todo-form>


        </div>


    </div>

</template>

<script type="text/javascript">


    import Vue from 'vue';
    import AddTodoForm from './AddTodoForm.vue'

    export default {
        components:{
            'todo-form':AddTodoForm
        },


        data(){
            return{
                title:"Todo Application with VueJS",
                count: 0,
                firstname:"",
                secondname :"",
                taskTitle:"",
                taskName:"",
                date: Date(),
                isEditing: false,
                todos:[{
                    id:1,
                    title:'Todo A',
                    Task:'project A',
                    date:'jun 30 2018',
                    done:false
                },
                    {
                        id:2,
                        title:'Todo B',
                        Task:'project B',
                        date:'jun 30 2018',
                        done:false
                    },{
                        id:3,
                        title:'Todo C',
                        Task:'project C',
                        date:'jun 30 2018',
                        done:false
                    }],

                apptitle:"Simple to do List",
                databinding:"Two way data binding",

            }

        },
        created() {
            this.$root.$on('taskAdded', (text) => {
               // this.title = text;
                this.todos.push(text);
            })
        },
        methods:{
            deleteTask(todo){
                console.log(todo);
                this.todos.pop(todo);
            }

        },
        computed:{

        }
    }

</script>