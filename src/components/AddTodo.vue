<template>
    <div>
        <form @submit="addTodo">
            <input type="text" class="form-control" v-model="title" name="title" placeholder="Write your task here">
            <br/>
            <button type="submit" class="btn btn-success" >Add task</button>
            <br/>
        </form>
    </div>
</template>

<script>
    import {v4 as uuid} from 'uuid';

    import 'bootstrap'
    import 'bootstrap/dist/css/bootstrap.min.css'

    /*
    This component handles the action of adding a new task to the todolist.

    A single todoitem consists of following properties:
        - id:                       Unique identifer, for which I used uuid() to generate every id
        - title:                    Describes the task and is used to display and identify the task for the user
        - completed:                A flag, which denotes whether a task has been completed or not. User is able to
                                    mark/unmark each todoitem via a checkbox as completed/uncompleted
     */

    export default {
        name: "AddTodo",
        data(){
            return{
                title: ""
            }
        },

        methods: {
            addTodo(e){
                /*
                Creates a new todoitem with the three properties.
                The completed flag is set to false when a new task is created, assuming a newly
                created task is unfinished originally.

                The object is then emitted and will be added to the array of todoitems in the App.vue component.

                Finally the title string is emptied.
                 */
                e.preventDefault();

                const newTodoObject = {
                    id: uuid(),
                    title: this.title,
                    completed: false,
                }

                this.$emit('add-todo', newTodoObject);
                this.title = "";
            }
        }
    }
</script>

<style scoped>
    .form-control{
        width: 300px;
        border-radius: 12px;
        border-color: white;
        box-shadow: 2px 2px 1px 1px grey;
    }

    input::-webkit-input-placeholder {
        color: gray;
        opacity: 0.5;
    }

    .btn {
        width: 130px;
        border-radius: 20px;
        color: white;
        background-color: #33ad02;
        margin-bottom: 40px;
    }
</style>