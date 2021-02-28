<template>
    <header>
        <h1>{{ title }} </h1>
        <Button @btn-click="$emit('show-add-task-form')" :text="showAddform ? 'Close' : 'Add Task'" :color="showAddform ? 'red' : 'green'" />        
    </header>
</template>

<script>
import Button from './Button'
export default {
    name: 'Header',
    props:{
        title: String,
        showAddform: Boolean
    },
    components: {
        Button
    },    
}
</script>

<style scoped>
header{
    display: flex;
    justify-content: space-between;
    align-items: center;
    margin-bottom: 20px ;
}
</style>