<script setup>
import { ref } from 'vue'

const props = defineProps({
    title: {
        type: String,
        default: ""
    },
    message: {
        type: String,
        default: ""
    }
})

</script>

<template>
    <h1>{{ title }}</h1>
    <h3>{{ message }}</h3>
 </template>

 <style scoped>
    h3 {
        width: 420px;
        line-height: 1.38rem;
        font-size: 1rem;
        margin-top: 20px;
    }
</style>
