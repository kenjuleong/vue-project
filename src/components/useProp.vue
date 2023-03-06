<script>
    import Button from './button.vue';
    export default {
        components: {
            Button
        },
        props: {
            name: {
                type: String,
                default: "Unknown User"
            },
            age: {
                type: Number,
                default: 0
            }
        },
        data: () => ({
            realAge: null
        }),
        emits: ['change-name', 'change-realAge'],
        methods: {
            changeAge() {
                this.$emit('change-realAge', this.realAge)
            }
        }
    }
</script>

<template>
    <h2>Use Prop</h2>
    <p>{{ name }} is {{ age }}</p>
    <input @change="changeAge" v-model="realAge" type="number">
<Button @click="$emit('change-name')">Emit Event (Toggle Name)</Button>
    <p v-if="age==0">Age is 0 because it was not binded/provided at App.vue</p>
</template>