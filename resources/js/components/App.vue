<template>
    <div class="todoListContainer">
        <div class="heading">
            <h2 id="title">Todo List</h2>
            <add-item-form/>
        </div>
        <list-view :items="items" />
    </div>
</template>

<script>
import addItemForm from "./AddItemForm";
import listView from "./ListView";

export default {
    components: {
        addItemForm,
        listView
    },
    data: function () {
        return {
            items: []
        }
    },
    methods: {
        getItemsList() {
            axios.get('api/items')
            .then(response => {
                this.items = response.data
            })
            .catch(error => {
                console.log(error);
            })
        }
    },
    created() {
        this.getItemsList();
    }
}
</script>

<style scoped>
    .todoListContainer {
        width: 350px;
        margin: auto;
    }

    .heading {
        background: #e6e6e6;
        padding: 10px;
    }

    #title {
        text-align: center;
    }
</style>
