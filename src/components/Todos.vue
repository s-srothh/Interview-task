<template>
    <div>
        <div id="incomplete">
            <h5 style="color: grey; opacity: 50%; text-align: left">Not finished Tasks</h5>
            <ul style="list-style: none; padding-left: 0px">
                <li v-bind:key="todo.id" v-for="todo in incompleteTasks">
                    <Todo v-bind:todo="todo" v-on:delete-todo="$emit('delete-todo', todo.id)"/>
                </li>
            </ul>
        </div>
        <div id="complete">
            <h5 style="color: grey; opacity: 50%; text-align: left">Finished Tasks</h5>
            <ul style="list-style: none; padding-left: 0px">
                <li style="opacity: 50%" v-bind:key="todo.id" v-for="todo in completeTasks">
                    <Todo v-bind:todo="todo" v-on:delete-todo="$emit('delete-todo', todo.id)"/>
                </li>
            </ul>
        </div>
    </div>
</template>

<script>
    import Todo from "./Todo";

    import 'bootstrap'
    import 'bootstrap/dist/css/bootstrap.min.css'

    /*
    This component takes care of displaying the todolist.

    The list is separated into two "classes" of tasks: Finished and Not Finished. This is done using
    computed values, which are described below.

    Handles the deletion of a todoitem by emitting the id of the item to the App.vue component.
     */

    export default {
        name: "Todos",
        components: {
            Todo
        },
        props: [
            "todos"
        ],

        computed: {
            incompleteTasks: function () {
                /*
                Filters the list of todos for the elements which have the completed flag set to false
                */
                return this.todos.filter(todo => todo.completed !== true);
            },
            completeTasks: function () {
                /*
                Filters the list of todos for the elements which have the completed flag set to false
                */
                return this.todos.filter(todo => todo.completed !== false);
            },
        },

    }
</script>

<style scoped>

</style>