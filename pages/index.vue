<!-- <template>
  <Tutorial/>
</template>

<script>
export default {
  name: 'IndexPage'
}
</script> -->


<template>
  <div>
    <h1>Blog Posts</h1>
    <ul>
      <li v-for="article of articles" :key="article.slug">
        <NuxtLink :to="{ name: 'blog-slug', params: { slug: article.slug } }">
          <img :src="article.img" />
          <div>
            <h2>{{ article.title }}</h2>
            <h3>{{ article.name }}</h3>
            <p v-if="article.author">By {{ article.author.name }}</p>
            <p v-else></p>
            <p>{{ article.description }}</p>
          </div>
        </NuxtLink>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  async asyncData({ $content, params }) {
    const articles = await $content("articles")
      .only(["title", "description", "img", "slug", "author", "name"])
      .sortBy("createdAt", "asc")
      .fetch();

    return {
      articles,
    };
  },
};
</script>

<style>
body {
  background-color: rgb(133, 207, 226);
  text-align: center;
}
li {
  list-style-type: none;
}
div {
  font-family: Helvetica;
}
</style>