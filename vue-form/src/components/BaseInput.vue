<script setup>

defineProps({
    label: {
        type: String,
        default: "",
    },
    modelValue: {
        type: String,
        default: "",
    }
});
defineEmits(['submit-text']);
</script>

<template>
    <div class="input-wrapper" >
       
        <label for="">{{ label }}</label>
        <input type="text" :value="modelValue" @input="$emit('update:modelValue', $event.target.value)">
        <button @click="$emit('submit-text')">Submit</button>
    </div>

</template>

<style lang="scss">
</style>