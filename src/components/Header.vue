<template>
    <div class="header">
        <h1>Todo List</h1>
    </div>
</template>


<script lang="ts">
import {Component, Prop, Vue} from 'vue-property-decorator';
@Component({
    name: "Header",
})
export default class extends Vue{
    
}
</script>

<style scoped>
.header{
    background: #333;
    color:#fff;
    text-align: center;
    padding:10px;
}

.header a {
    color:#fff;
    padding-left: 5px;
}
</style>