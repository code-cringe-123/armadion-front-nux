<template>
  <div class="blog-container">
    <div class="blog-wrapper">
      <div class="blog-title">Из Блога</div>
      <div class="posts-wrapper">
        <!-- <div
          class="posts"
          :class="{
            'posts-active': isActivePost || index1 < 2,
            'posts-inactive': !isActivePost && index1 >= 2,
          }"
          v-for="(post, index1) in posts"
          :key="post.id"
        >
          <Post :post="post" />
        </div> -->
        <div class="posts" v-for="(post, index) in posts" :key="post.id">
          <Post :post="post" />
        </div>
      </div>
      <div style="margin-top: 20px" class="postsvideo-wrapper">
        <div
          class="postsvideo"
          v-for="(postvideo, i) in postsvideo"
          :key="postvideo.id"
        >
          <PostVideo :postvideo="postvideo" />
        </div>
      </div>
      <!-- <ViewMoreButton
        @click="toggleActivePost"
        :class="{ 'posts-btn': isActivePost }"
        >Смотреть все</ViewMoreButton
      > -->
    </div>
  </div>
</template>

<script setup>
import { ref, onMounted } from "vue";
const isActivePost = ref(false);

// const toggleActivePost = () => {
//   isActivePost.value = !isActivePost.value;
// };

const posts = ref([]);
const postsvideo = ref([]);
// загрузка данных из products.json
const loadPosts = async () => {
  try {
    const responsePosts = await fetch("/posts.json");
    const responseDataPosts = await responsePosts.json();
    posts.value = responseDataPosts;

    const responsePostsVideo = await fetch("/postsvideo.json");
    const responseDataPostsVideo = await responsePostsVideo.json();
    postsvideo.value = responseDataPostsVideo;
  } catch (error) {
    console.error("Ошибка загрузки данных:", error);
  }
};

onMounted(() => {
  loadPosts();
});
</script>

<style lang="scss">
.posts-inactive,
.posts-btn {
  display: none !important;
}

.blog-container {
  width: 100%;
  display: flex;
  align-items: center;
  justify-content: center;
  margin-top: 80px;

  @media screen and (max-width: 768px) {
    width: 100vw;
    margin-top: 120px;
  }
}

.blog-wrapper {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  max-width: 1180px;

  @media screen and (max-width: 1024px) {
    width: 100vw;
  }
}

.posts-wrapper,
.postsvideo-wrapper {
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  gap: 20px;

  @media screen and (max-width: 1024px) {
    display: grid;
    grid-template-columns: repeat(1, 1fr);
    gap: 20px;
  }
}

.blog-title {
  font-size: 36px;
  font-weight: 400;
  width: 1180px;
  margin-bottom: 40px;
  color: #111827;
  line-height: 38px;

  @media screen and (max-width: 1200px) {
    width: 96vw;
  }

  @media screen and (max-width: 768px) {
    width: 355px;
    font-size: 24px;
    font-weight: 400;
    line-height: 25px;
  }
}
</style>
