<script setup>
import news from "../json/news.json";
</script>

<template>
  <div class="content">
    <div style="padding-top 1.5em;padding-bottom: 1.5em;">
      <h1 class="m-0">welcome</h1>
      <h3 class="m-0 color-gray">com-sci</h3>
    </div>
    
    <hr />

    <h5>News</h5>
    <article>
      <table>
        <thead>
          <tr>
            <th>Date</th>
            <th>Heading</th>
          </tr>
        </thead>
        <tbody>
          <tr v-for="news_content in news" :key="news_content.newsId">
            <td class="date">{{ news_content.News_Date }} </td>
            <td class="title">{{ news_content.News_Title }}</td>
          </tr>
        </tbody>
      </table>
    </article>
  </div>
</template>
<style scoped>
.content {
  margin-top: 1em;
  margin-bottom: 1em;
}

.header { 
  display: flex;
  align-items: center;
  padding: 1.5em 0;
}

.title {
  margin: 0;
}

.subtitle {
  color: gray;
  margin: 0;
}

.date {
  text-align: left;
}

.title {
  text-align: left;
}
</style>
