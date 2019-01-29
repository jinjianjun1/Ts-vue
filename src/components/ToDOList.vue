<template>
    <div>
        <ol>
            <li v-for="(item,index) in list " :key="index">
                <label >
                    <input type="checkbox" :checked="item.status===1"
                    @change="changeStatus(item,$event)">
                </label>
                {{item.name}}
            </li>
        </ol>
    </div>
</template>

<script lang="ts">
    import {Component,Vue} from 'vue-property-decorator'
    import Todo from '../modules/Todo'

    @Component({
        props:{
            list:Array
        }
    })
    export default class ToDOList extends Vue {
        changeStatus(item:Todo,e:Event){
            let checked=(<HTMLInputElement>e.target).checked;
            this.$emit('changeTodo',item,{status:checked?1:2});

        }
    }
</script>

<style scoped lang="scss">

</style>