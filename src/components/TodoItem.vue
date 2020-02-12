<template>
    <div v-bind:class="{'isComplete':todo.isDone}">
        <ul>
            <li><input type="checkbox" v-on:change="TaskDone"><label v-on:click="editTodo">{{todo.title}}</label></li>
            <button v-on:click="$emit('del-todo', todo.id)">DELETE ME</button>
        </ul>	
    </div>
</template>

<script>


export default {
    name:'TodoItem',

    props:["todo"],
    methods: {
        TaskDone(){
          this.todo.isDone = !this.todo.isDone
		},
		editTodo(){
			this.todo.isEditing = !this.todo.isEditing

		}
    },

}
</script>

<style scoped>
ul {
    list-style-type:none;
}
.isComplete ul li{
    text-decoration: line-through;
}
</style>