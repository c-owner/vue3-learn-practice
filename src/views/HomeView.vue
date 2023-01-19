<script setup>
import { useRouter } from 'vue-router';

const router = useRouter();
const goAboutPage = () => {
    router.push('/about');
};
</script>

<template>
    <div>
        <h2>Home View</h2>
        <p>
            <button class="btn btn-primary" @click="goAboutPage">About</button>
        </p>
    </div>
</template>

<style scoped></style>
