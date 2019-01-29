<template>
    <div class="todolist">
        <input type="text" v-model="text">
        <button @click="addList">添加</button>
    </div>
</template>

<script lang="ts">
    import {Component,Vue,Mixins} from 'vue-property-decorator'
    @Component

    export default class NewToDo extends Vue {
        text='';
        addList() {
            this.$emit('addList',this.text)
            this.text=''
        }
    }
</script>

<style scoped lang="scss">
.todolist{

}
</style>