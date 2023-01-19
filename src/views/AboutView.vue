<script setup>
import { useRoute } from 'vue-router';

const route = useRoute();
console.log(route.name);
</script>

<template>
    <div>
        <h2>About View</h2>
        <p>{{ $route.path }}</p>
        <p>{{ $route.name }}</p>
        <button class="btn btn-primary" @click="$router.push('/')">Home</button>
    </div>
</template>

<style scoped></style>
