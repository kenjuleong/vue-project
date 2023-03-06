<template>
<div style="border: 5px solid white">
<h1 class="h1"><slot name="title" /></h1>
<p class="p"><slot name="description" /></p>
</div>
</template>

<style>
    .h1,.p {
        font-family: monospace;
        color: grey;
    }
</style>