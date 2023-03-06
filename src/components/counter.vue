<script>    
import Button from './button.vue';
    export default {
        components: {
            Button
        },
        props: ["list"],
        data() {
            return {
                count: 1
            }
        },
        methods: {
increase() {
    this.count++;
}
}
    }
</script>

<template>
    <h1>{{ count }}</h1>
    <p>There are {{ list.length }} of people</p>
    <p v-if="count % 2 == 0">This is an even number</p>
    <p v-else>This is an odd number</p>
    <Button @click="increase">Increase</Button>
</template>