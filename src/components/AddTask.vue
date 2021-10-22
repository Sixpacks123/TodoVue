<!--Addtask-->
<template>
<div>
    <div id="AddTask">
        <div class="row" style="margin-top:100px;">
            <div class="col-1 col-md1 col-lg-2"></div>
            <div class="col-10 col-md-9 col-lg-7" >
                <div class="line">
                    <input
                    type = "text"
                    class="text-line"
                    placeholder="Add task here"
                    v-model="newTodo"
                    @keyup.enter="addTodo"
                    maxlength="30"
                    />
                </div>
                <div class="col-2 col-md-3"></div>
            </div>
        </div>
    </div>
</div>
</template>


<script>
export default {
    name : "AddTask",

    //return Data 
    data(){
        return{
            todos: todoStorage.fetch(),
            newTodo : ""
        }
    },methods: {
        addTodo(){
            const todoValue = this.newTodo && this.newTodo.trim()
            if(!todoValue){
                return;
            }
            this.todos.push({
                id: todoStorage.uid++,
                title : todoValue,
                favourite : false,
                completed : false
            });

            this.newTodo = " "
        }
    }
}
</script>