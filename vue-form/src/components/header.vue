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
        width: 356px;
        line-height: 1.25rem;
        font-size: 16px;
    }
</style>
