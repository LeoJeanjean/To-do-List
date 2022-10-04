<template>
    <div class="tab-content" id="ex1-content">
        <div class="tab-pane fade show active" id="ex1-tabs-1" role="tabpanel" aria-labelledby="ex1-tab-1">
            <ul class="list-group mb-0">
                <li class="list-group-item d-flex align-items-center border-0 mb-2 rounded" style="background-color: #f4f6f7;">
                    <input class="form-check-input me-2 help" type="checkbox" value="" aria-label="..." unchecked @click="TaskDone"/>
                    <span>{{itemDesc}}</span>
                    <button class="remove" @click="RemoveItem" type="button">X</button>
                </li>
            </ul>
        </div>
    </div>
</template>

<script>
    export default {
        name: "TodoListItem",
        props: {
            itemDesc: String
        },
        methods: {
            RemoveItem() {
                this.$emit('remove-item');
            }
        },
        data() {
            return;
        }
    }
</script>

<style scoped>
.remove {
    margin-left: auto;
    font-size: bold;
    background-color: transparent;
    border: none;
    cursor: pointer;
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
</style>