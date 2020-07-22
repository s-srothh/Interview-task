<template>
    <div class="alert alert-info alert-dismissible" role="alert">
        <div v-bind:class="{ 'completed': todo.completed }" style="text-align: left;">

            <input v-on:click="markComplete" type="checkbox" id="exampleCheck1" class="form-check-input"
                   v-model="this.todo.completed">

            <p style="font-size: 18px; padding-left: 10px">{{ todo.title }}</p>
            <button @click="$emit('delete-todo', todo.id)" type="button" class="close"  aria-label="Close" style="display: block">
                <span aria-hidden="false">&times;</span></button>

        </div>
    </div>
</template>

<script>
    import 'bootstrap'
    import 'bootstrap/dist/css/bootstrap.min.css'

    /*
    This component takes care of displaying the todoitems. As a starting point bootstrap styles have been
    used, and then altered.

    Consists of a single method. Which sets the completed flag of each item, based on the state of the checkbox.
     */


    export default {
        name: "Todo",
        props: [
            "todo"
        ],
        methods: {
            markComplete() {
                /*
                Handles the toggling of the checkbox between checked and unchecked.
                Simply negates the current state of the checkbox when clicked.
                 */
                this.todo.completed = !this.todo.completed;
            }
        }
    }
</script>

<style scoped>
    /*
    When task is completed, title text is crossed out.
    */
    .completed {
        text-decoration: line-through;
    }

    .alert {
        width:300px;
        height: 55px;
        border-radius: 1px;
        border-color: white;
        color: black;
        background-color: white;
        box-shadow: 2px 3px 2px 2px grey;

    }

    .form-check-input {
        width: 20px;
        height: 20px;
    }

</style>