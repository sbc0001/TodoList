<template>
    <div>
        <h1>할 일 목록</h1>
        <input type="text" 
                v-model="newTodo" 
                @keyup.enter="addTodo" 
                placeholder="해야할 일을 입력해주세요."
        />
        <button @click="addTodo"> 입력 </button>
        <ul>
            <TodoItem 
                v-for="(todo,index) in todos" 
                :key="index" 
                :todo="todo" 
                @toggle="toggleTodo"
            />
        </ul>
        <button @click="removeChecked">완료 삭제</button>
    </div>
</template>
<script>
import TodoItem from './TodoItem.vue';

export default{
    components:{
        TodoItem
    },
    data(){
        return{
            newTodo:'',
            todos:[],
        }
    },
    created(){
        const storedTodos=localStorage.getItem('todos');
        if(storedTodos){
            this.todos=JSON.parse(storedTodos);
        }
    },
    methods:{
        savedTodos(){
            localStorage.setItem('todos',JSON.stringify(this.todos));
            // sessionStorage
        },
        addTodo(){
            if(this.newTodo.trim()){
                this.todos.push({
                    text:this.newTodo.trim(),
                    checked: false
                });
                this.newTodo='';
                this.savedTodos();
            }
        },
        toggleTodo(todo){
            todo.checked = !todo.checked;
            this.savedTodos();
        },
        removeChecked(){
            this.todos = this.todos.filter(todo => !todo.checked);
            this.savedTodos();
        }
    }
}
</script>
<style scoped>
    h1{
        margin:10px 0;
        padding-top:10px;
    }
    button{
        padding:5px 10px;
        border:0 none;
        background-color:#227394;
        color:#fff;
        font-weight:bold;
        font-size:1.1rem;
        border-radius:10px;
        margin-left:10px;
        box-shadow:4px 5px 4px rgba(0,0,0,0.3);
    }
    input{
        min-width:200px;
        height:35px;
        padding:5px;
        margin-bottom:10px;
        box-sizing:border-box;
    }
    ul{
        counter-reset:index 0;
        position:relative;
    }
</style>