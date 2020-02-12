<template>
    <div>
        <input type="text" v-model="title" @keyup.enter='addTodo' placeholder="What is your next task ?"/>
    </div>
</template>

<script>
import uuid from 'uuid';
export default {
    name:'AddTodo',
    data() {
        return {
            title: '',
            id:''
        }
    },
    methods: {
        addTodo(){
            
            const newTodo = {
                id: uuid.v4(),
                title:this.title,
                isDone: false,
                isEditing:false
            }
            this.title = "";
            this.$emit('addTodo', newTodo);
        }
        
    }

}
</script>

<style>

</style>