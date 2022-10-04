<template>
    <section class="listContainer1">
        <div class="container py-5 h-100 listContainer2">
            <div class="row d-flex justify-content-center align-items-center h-100 list">
                <div class="col col-xl-10">
                    <div class="card">
                        <div class="card-body p-5">
                            <span class="list-name">{{listName}}</span>
                            <button class="remove" @click="RemoveList" type="button">X</button>

                            <form class="d-flex justify-content-center align-items-center mb-4">
                                <div class="form-outline flex-fill input-container">
                                    <input type="text" id="form2" class="form-control help" v-model="newItem"/>
                                    <button type="button" class="btn btn-info ms-2" @click="AddItem">+</button>
                                </div>
                            </form>

                            <div>
                                <ul class="list-group mb-0">
                                    <li class="list-group-item" style="background-color: #f4f6f7;" v-for="(item, index) in items" :key="item">
                                        <TodoListItem v-bind:itemDesc="item" @remove-item='RemoveItem(index)'/>
                                    </li>
                                </ul>
                            </div>

                        </div>
                    </div>
                </div>
            </div>
        </div>
    </section>
</template>

<script>
import TodoListItem from './TodoListItem.vue';
export default {
    name: "TodoList",
    components: { TodoListItem },
    data: function() {
        return {
            items: [],
            newItem: ""
        }
    },
    methods: {
        AddItem() {
            this.items.push(this.newItem);
            this.newItem = "";
        },
        RemoveItem(itemIndex) {
            this.items.splice(itemIndex, 1);
        },
        RemoveList() {
                this.$emit('remove-list');
            },
    },
    props: {
        listName: String
    }
};
</script>

<style>
.list{
    width: 80%;
}
.listContainer1{
    width: 100%;
}
.listContainer2{
    display: flex;
    justify-content: center;
    padding-bottom: 0px !important;
}
.remove{
    position: absolute;
    top: 0%;
    right: 0%;
    font-weight: bold;
    border: none;
    background-color: white;
}
.input-container{
    display: flex;
    border: 1px solid #ced4da;
    width: 100%;
    font-size: 1rem;
    font-weight: 400;
    line-height: 1.5;
    color: #212529;
    background-color: #fff;
    -webkit-appearance: none;
    -moz-appearance: none;
    appearance: none;
    border-radius: 0.375rem;
}
.help{
    outline:0px !important;
    -webkit-appearance:none;
    box-shadow: none !important;
    border: none !important;
}
input:focus, textarea:focus, select:focus{
        outline: none !important;
        -webkit-appearance:none;
}
.list-name{
    position: absolute;
    top: 0px;
    left: 0px;
    margin: 5px
}
</style>