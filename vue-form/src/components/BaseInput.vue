<script setup>

defineProps({
    firstName: {
        type: String,
        default: ""
    },
    lastName: {
        type: String,
        default: ""
    },
    email: {
        type: String,
        default: ""
    },
    password: {
        type: String,
        default: ""
    }
});
defineEmits(['update:firstName', 'update:lastName', 'update:email', 'update:submitEvent']);



</script>

<template>
    <form action="" @submit.prevent="$emit('update:submitEvent')">
        <div class="input-wrapper" >
        <input type="text" :value="firstName" @input="$emit('update:firstName', $event.target.value)" placeholder="First Name">
        <p class="error">Error!</p>
        </div>    

        <div class="input-wrapper">
            <input type="text" :value="lastName" @input="$emit('update:lastName', $event.target.value)" placeholder="Last Name">
            <p class="error">Error!</p>
        </div>

        <div class="input-wrapper">
            <input type="text" :value="email" @input="$emit('update:email', $event.target.value)" placeholder="Email Address">
            <p class="error">Error!</p>
        </div>
        <button>Submit</button>
    </form>
    
    

</template>

<style scoped>
    .input-wrapper {
        display: flex;
        flex-direction: column;
        justify-content: space-between;
        align-items: flex-start;
        width: 420px;
        margin-bottom: 1.4em;
    }

    input,
    button {
        border: 1px solid  rgba(149, 157, 165, 0.2);
        border-radius: 8px;
        width: 100%;
        padding: 1rem;
        font-size: 1rem;
    }

    button {
        cursor: pointer;
        width: 100%;
        background-color:rgb(231, 106, 106);
        color: white;
        font-weight: bold;
        
    }

    .error {
        display: none;
    }

</style>