<script setup>
import { useRouter, useRoute } from 'vue-router';
import { getPostById } from '@/api/posts';
import { ref } from 'vue';

const route = useRoute();
const router = useRouter();
const id = route.params.id;
const form = ref({});
// let form = reactive({});
/*
 * 반응형 기초를 배울때 string, number는 ref로 선언
 * 배열이나 객체와 같은 것은 reactive 함수로 선언
 * 그렇지만 form을 ref 객체로 선언했던 이유는
 * ref로 선언하면 장점은 ...data 처럼 한꺼번에 객체 복사를 할 수 있다.
 * reactive는 하나씩 속성과 값을 집어 넣어주어야 한다. (한꺼번에 넣을 경우 일반 객체 값으로 들어가며, 주소값이 달라 value를 사용할 수 없다.
한꺼번에 넣어 반응형을 상실하게 될 경우, vue Devtools에서 확인해보면 수정할 수 없어진다.
 * */

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
