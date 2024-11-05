<template>
    <li :class="{checked:todo.checked}">
        <input type="checkbox" @change="toggleCheck" :checked="todo.checked"> {{ todo.text }} 
    </li>
</template>

<script>
export default{
    props:{
        todo:{
            type:Object, // type:String에서 변경 -- text:string, checked:boolean 상태 필요
            required:true,
        },
    },
    methods:{
        toggleCheck(){
            this.$emit('toggle', this.todo); // 부모 자식 간 데이터 전달
            //this.todo.checked;
            //console.log(this.todo.checked);
        },
    }
}
</script>
<style scoped>
    input{
        width:15px;
        height:15px;
        position:absolute;
        left:40px;
    }
    li:before{
        content:counter(index)".";
        margin-left:5px;
    }
    li{
        counter-increment:index;
        font-size:1.2rem;
        font-weight:bold;
        border-top:2px dashed #514fc0;
        border-bottom:2px dashed #514fc0;
        padding:10px 30px;
        margin-bottom:15px;
        display:flex;
        justify-content:space-between;
        align-items:center;
        text-shadow:4px 5px 4px rgba(0,0,0,0.3);
    }
    button{
        padding:5px 10px;
        border:0 none;
        background-color:#227394;
        color:#fff;
        font-weight:bold;
        font-size:1.1rem;
        border-radius:10px;
        box-shadow:4px 5px 4px rgba(0,0,0,0.3);
    }
</style>