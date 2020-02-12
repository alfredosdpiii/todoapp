<template>
    <div v-bind:class="{'isComplete':todo.isDone}">
        <ul>
            <li>
                <input v-if="this.todo.isEditing" type="text"  @keydown.esc="resetEditting" @keyup.enter="edit">
                <input v-if="!this.todo.isEditing" type="checkbox" v-on:click="TaskDone">
                <span v-on:click="editTodo" >{{todo.title}}</span>
                <button  v-if="!this.todo.isEditing" v-on:click="$emit('del-todo', todo.id)">DELETE ME</button>
            </li>
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
        },

        resetEditting(){
			this.todo.isEditing = false;
        },
        edit(){
            console.log('edit')
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