<template>
    <div class="d-flex flex-column">
        <draggable :list="list" :group="groupName" @change="OnInput" class="drag-container">
            <b-card
                    v-for="listItem in list"
                    :key="listItem.id"
                    bg-variant="default"
                    :header="listItem.title"
                    class="text-center"
            >
                <b-card-text>{{listItem.description}}</b-card-text>
            </b-card>
        </draggable>
    </div>
</template>

<script>
    import draggable from 'vuedraggable'

    export default {
        name: "Dashboard-column",
        props: {
            list: Array,
            groupName: String,
            title: String
        },
        components: {
            draggable
        },
        methods: {
            OnInput(item) {
                if (item.added) {
                    this.$emit('add', item.added.element)
                }
            }
        }
    }
</script>

<style scoped>
.drag-container {
    min-height: 50vh;
}

.card + .card {
    margin-top: 10px;
}
</style>
