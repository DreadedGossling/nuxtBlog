<template>
  <article>
    <h1>{{ article.title }}</h1>
    <p>{{ article.description }}</p>
    <img :src="article.img" :alt="article.alt" />
    <p>Article last updated: {{ formatDate(article.updatedAt) }}</p>

    <nuxt-content :document="article" />

    <author :author="article.author" />

    <prev-next :prev="prev" :next="next" />

    <!-- <pre>{{article}}</pre> -->

    <AppSearchInput />
  </article>
</template>


<!-- <template>
  <article>
    <h1>{{ article.title }}</h1>
    <p>{{ article.description }}</p>
    <img :src="article.img" :alt="article.alt" />
    <p>Article last updated: {{ formatDate(article.updatedAt) }}</p>

    <nuxt-content :document="article" />

    <author :author="article.author" />
  </article>
</template> -->

<script>
export default {
  async asyncData({ $content, params }) {
    const article = await $content('articles', params.slug).fetch()

    const [prev, next] = await $content('articles')
      .only(['title', 'slug'])
      .sortBy('createdAt', 'asc')
      .surround(params.slug)
      .fetch()

    return {
      article,
      prev,
      next
    }
  },
  methods: {
    formatDate(date) {
      const options = { year: "numeric", month: "long", day: "numeric" };
      return new Date(date).toLocaleDateString("en", options);
    },
  },
};
</script>

<style>
  .nuxt-content h2 {
    font-weight: bold;
    font-size: 28px;
  }
  .nuxt-content h3 {
    font-weight: bold;
    font-size: 22px;
  }
  .nuxt-content p {
    margin-bottom: 20px;
  }
  .text {
    background-color: blue;
    color: white;
    padding: 4px;
    margin-bottom: 4px;
  }
  /* info-box{
    background-color: red;
    color: black;
    padding: 4px;
  } */
  .icon.icon-link {
  background-image: url('~assets/svg/icon-hashtag.svg');
  display: inline-block;
  width: 20px;
  height: 20px;
  background-size: 20px 20px;
}
</style>



<!-- <template>

<article>

<nav>
<ul>
<li v-for="link of article.toc" :key="link.id">
<NuxtLink :to="`#${link.id}`">{{ link.text }}</NuxtLink>
</li>
</ul>
</nav>
<!-- <pre> {{ article }} </pre> -->

<!-- <p>Post last updated: {{ article.updatedAt }}</p>

<h1>{{ article.title }}</h1>
<p>{{ article.description }}</p>
<!-- <img :src="~assets/images/article.jpeg" :alt="article.alt" /> -->

<!-- <nuxt-content :document="article" />

<p>Article last updated: {{ formatDate(article.updatedAt) }}</p>

</article>

</template> -->

