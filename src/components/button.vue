<script>
    export default {
        props: {
            color: {
                type: String,
                default: "black"
            }
        }
    }
</script>
<template>
    <button style="background-color: black; padding:10px; color: white; border: 0; border-radius: 5px; margin: 5px;">
    <slot>Button</slot>
    </button>
</template>