<script>
    import Button from './button.vue';
    export default {
        components: {
            Button
        },
        props: {
            index: {
                type: Number,
                required: true
            },
            i: {
                type: Object,
                required: true
            }
        },
        emits: ["delete-people"],
        methods: {
            deletePeople(name) {
                this.$emit('delete-people', name)
            }
        }
    }
</script>

<template>
{{ index + 1 }}. {{ i.name }} has {{ i.attack }} attack & {{ i.health }} health <Button @click="deletePeople(i.name)">Delete</Button>
</template>