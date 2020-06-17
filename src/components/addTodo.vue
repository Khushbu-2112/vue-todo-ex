<template>
    <div>
        <form @submit.prevent="$emit('add-todo',title)">
            <input type="text"  placeholder="add title" v-model="title" name="title">
            <input type="submit" value="Submit" class="btn">
        </form>
    </div>
</template>

<script>
export default {
    name:"addTodo",
    data() {
        return {
            title:''
        }
    },
    methods: {
        clear(){
            this.title='';
        }
    },
}
</script>

<style scoped>
    .btn{
        background: #41B883;
        color: #34495E;
        margin: 2%;
        padding: 5px;
        border: none;
        font-weight: bold;
        border-radius: 5px;
    }

    form{
        margin:2% 10%;
    }

</style>