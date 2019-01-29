<template>
    <div class="app">
        <div class="index">
            <NewTodo @addList="addList"></NewTodo>
            <ToDolist :list="list" @changeTodo="changeTodo"></ToDolist>
        </div>
    </div>
</template>

<script lang="ts">
    import {Component, Vue,Mixins} from 'vue-property-decorator';
    import {Mixin1} from  "./mixins/mixin-1"
    import NewTodo from './components/NewToDo.vue'
    import  ToDolist from './components/ToDOList.vue'
    import Todo from './modules/Todo'

    @Component({
        components: {
            NewTodo,ToDolist
        },
        watch:{
            list(newValue:Array<Todo>){
                console.log(newValue);
                let string=JSON.stringify(newValue);
                localStorage.setItem('data',string)
            }
        }
    })
    export default class App extends Vue{
        list:Array<Todo>=localStorage.getItem('data')?JSON.parse(<string>localStorage.getItem('data')):[];
        addList(name:string){
          let todo:Todo={name:name,status:1};
          this.list.push(todo)
        }
        changeTodo(todo:Todo,part:Partial<Todo>){
            let index:number =this.list.indexOf(todo)
            let newItem:Todo =Object.assign(todo,part)
            this.list.splice(index,1,newItem)
        }
    }

</script>

<style lang="scss" scoped>
    .app {
        border: 1px solid red;
        font-size: 36px;
        display: flex;
        align-items: center;
        justify-content: center;
        .index{
        }
    }
</style>
<style lang="scss">
    *{margin: 0;padding: 0;}
    ol,ul{list-style: none}

</style>