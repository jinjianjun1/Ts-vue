<template>
    <div>
        <ol>
            <li v-for="(item,index) in list " :key="index">
                {{item.name}}
            </li>
        </ol>
    </div>
</template>

<script lang="ts">
    import {Component,Vue} from 'vue-property-decorator'

    @Component({
        props:{
            list:Array
        }
    })
    export default class ToDOList extends Vue {

    }
</script>

<style scoped lang="scss">

</style>