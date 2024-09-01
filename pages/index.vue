<template>
  <main class="container">
    <template v-if="error">Error: {{ error.message }}</template>
    <template v-else-if="isEmptyPostList">
      블로그 글이 존재하지 않습니다.
    </template>
    <template v-else>
      <section class="wrapper">
        <v-card
          v-for="(post, i) in postList"
          :key="i"
          elevation="4"
          rounded="lg"
          class="card-wrapper"
          @click="router.push(`/${post.id}`)"
        >
          <v-card-item>
            <v-card-title>{{ post.title }}</v-card-title>
          </v-card-item>
          <v-card-text class="description">{{ post.description }}</v-card-text>
          <v-card-text class="date">{{ post.date }}</v-card-text>
        </v-card>
      </section>
    </template>
  </main>
</template>
<script setup lang="ts">
import type { ParsedContent } from '@nuxt/content';

const router = useRouter();

interface PostTypes extends ParsedContent {
  id: number;
  title: string;
  date: string;
  description: string;
}

const isEmptyPostList = ref<Boolean>(false);
const postList = ref<PostTypes[]>([]); // 빈 배열은 모든 배열의 기본 상태로 간주

const { error, data } = await useAsyncData<PostTypes[]>('posts', () =>
  queryContent<PostTypes[]>('/').find()
);

// const data = await queryContent('/').find();

if (!data.value) {
  console.log('블로그 글이 존재하지 않습니다.');
  isEmptyPostList.value = true;
} else {
  postList.value = data.value.map((item: PostTypes) => ({
    id: item.id,
    title: item.title,
    date: item.date,
    description: item.description,
  }));
  console.log('postList => ', postList);
}
</script>

<style scoped lang="scss">
@import '@/assets/styles/main.scss';
.container {
  .wrapper {
    display: grid;
    grid-template-columns: 1fr 1fr 1fr 1fr;
    gap: 20px;
    .card-wrapper {
      height: 160px;
      &:hover {
        // background-color: $main-color;
        // color: $white-color;
        // transition: background-color 0.3s ease;

        cursor: pointer;
      }
      .description {
        height: 58px;
        display: -webkit-box;
        -webkit-line-clamp: 3;
        -webkit-box-orient: vertical;
        overflow: hidden;
        text-overflow: ellipsis;
        font-size: $medium-font-size;
        padding-bottom: 0px;
      }
      .date {
        text-align: end;
        padding-bottom: 0px;
        font-size: $medium-font-size;
      }
    }
  }
}
</style>
