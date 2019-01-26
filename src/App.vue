<template>
    <div class="app">
        <div class="index">
            <NewTodo @addList="addList"></NewTodo>
            <ToDolist :list="list"></ToDolist>
        </div>
    </div>
</template>

<script lang="ts">
    import {Component, Vue,Mixins} from 'vue-property-decorator';
    import {Mixin1} from  "./mixins/mixin-1"
    import NewTodo from './components/NewToDo.vue'
    import  ToDolist from './components/ToDOList.vue'
    interface Todo{
        name:string
        status:1|2|3
    }
    @Component({
        components: {
            NewTodo,ToDolist
        },
    })
    export default class App extends Vue{
        list:Array<Todo>=[
            {name:'任务1',status:1},
            {name:'任务2',status:2},
            {name:'任务3',status:3}
        ];
        addList(name:string){
          let todo:Todo={name:name,status:1};
          this.list.push(todo)
        }
    }

</script>

<style lang="scss">
    .app {
        display: flex;
        align-items: center;
        justify-content: center;
        .index{
        }
    }
</style>
