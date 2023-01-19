<script setup>
import PostItem from '@/components/posts/PostItem.vue';
</script>

<template>
    <div>
        <h2>게시글 리스트</h2>
        <hr class="my-4" />
        <div class="row g-3">
            <div class="col-12" v-for="(i, index) in 10" :key="index">
                <PostItem title="제목" content="내용" created-at="2023-01-19" />
            </div>
        </div>
    </div>
</template>

<style scoped></style>
