<template>
    <b-row class="Dashboard">
        <b-col>
            <DashboardCol
                    title="Открыта"
                    :group-name="groupName"
                    :list="opened"
                    @add="ChangeStatusTo('opened', $event)"
            />
        </b-col>
        <b-col>
            <DashboardCol
                    title="В работе"
                    :group-name="groupName"
                    :list="working"
                    @add="ChangeStatusTo('working', $event)"
            />
        </b-col>
        <b-col>
            <DashboardCol
                    title="Закрыта"
                    :group-name="groupName"
                    :list="closed"
                    @add="ChangeStatusTo('closed', $event)"
            />
        </b-col>
    </b-row>
</template>

<script>
import DashboardCol from './Dashboard-column'
export default {
    name: "Dashboard",
    components: {
        DashboardCol
    },
    props: {
        tasks: Array
    },
    computed: {
        opened() {
            return this.tasks.filter(({ status }) => status === 'opened' )
        },
        closed() {
            return this.tasks.filter(({ status }) => status === 'closed' )
        },
        working() {
            return this.tasks.filter(({ status }) => status === 'working' )
        }
    },
    data() {
        return {
            groupName: 'tasks'
        }
    },
    methods: {
        ChangeStatusTo(status, item) {
            const itemCopy = { ...item, status };
            const itemIndex = this.tasks.findIndex(task => task.id === itemCopy.id);
            const tasksCopy = [...this.tasks];
            tasksCopy.splice(itemIndex, 1, itemCopy)
            this.$emit('update:tasks', tasksCopy)
        }
    }
}
</script>

<style scoped>
.Dashboard .col {
    border: 1px black solid;
    padding: 10px;

}
.Dashboard .col + .Dashboard .col {
    margin-left: 10px;
}
</style>
