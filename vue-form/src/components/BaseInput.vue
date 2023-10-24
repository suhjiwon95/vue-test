<script setup>

defineProps({
    firstName: {
        type: String,
        default: ""
    }
});
defineEmits(['update:firstName', 'update:submitHandler']);



</script>

<template>
    <div class="input-wrapper" >
        <label for="">First name</label>
        <input type="text" :value="firstName" @input="$emit('update:firstName', $event.target.value)">
        <button @click="$emit('update:submitHandler')">Submit</button>
    </div>

</template>

<style lang="scss">
</style>