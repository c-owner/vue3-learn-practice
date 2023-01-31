<script setup>
import { useRouter, useRoute } from 'vue-router';
import { getPostById } from '@/api/posts';
import { ref } from 'vue';

const route = useRoute();
const router = useRouter();
const id = route.params.id;
/*
 * ref
 * 장점 ) 객체 할당 가능, 일관성 유지 (페이지 컴포넌트에서는 ref를 사용하는 편이다. 그렇지만 보통 회사의 컨벤션을 따르는게 맞다. 이것이 정답은 아님 )
 * 단점 ) form.value.title, form.value.content 특정 속성 값을 넣을 때 불편함
 *
 * reactive
 * 단점 ) 객체 할당 불가능
 * 장점 ) form.title, form.content 특정 속성 값을 넣을 때 편리함
 * */
const form = ref({});
// let form = reactive({});

const fetchPost = () => {
    const data = getPostById(id);
    form.value = { ...data }; // 개체 복사
    // form = { ...data }; // reactive에서 개체 복사를 하면 반응형을 상실한다.
    // form.title = data.title;
    // form.content = data.content;
    // form.createdAt = data.createdAt;
};
fetchPost();

const goListPage = () => {
    router.push({
        name: 'PostList'
    });
};

const goEditPage = () => {
    router.push({
        name: 'PostEdit',
        params: {
            id
        }
    });
};
</script>

<template>
    <div>
        <h2>{{ form.title }}</h2>
        <p>{{ form.content }}</p>
        <p class="text-muted">{{ form.createdAt }}</p>
        <hr class="my-4" />
        <div class="row g-2">
            <div class="col-auto">
                <button class="btn btn-outline-dark">이전글</button>
            </div>
            <div class="col-auto">
                <button class="btn btn-outline-dark">다음글</button>
            </div>
            <div class="col-auto me-auto"></div>
            <div class="col-auto">
                <button class="btn btn-outline-dark" @click="goListPage">목록</button>
            </div>
            <div class="col-auto">
                <button class="btn btn-outline-primary" @click="goEditPage">수정</button>
            </div>
            <div class="col-auto">
                <button class="btn btn-outline-danger">삭제</button>
            </div>
        </div>
    </div>
</template>

<style scoped></style>
