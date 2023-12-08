<template>
  <section>
    <ul>
      <li v-for="post in data" :key="post._path">
        <NuxtLink :to="post._path">
          {{ post.title }}
        </NuxtLink>
      </li>
    </ul>
  </section>
</template>

<script setup>
const { data } = await useAsyncData("blog-list", () =>
  queryContent("/blog").only(["_path", "title"]).find()
);

console.log(data.value);
</script>
