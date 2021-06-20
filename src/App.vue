<template>
  <h1>Twotter</h1>
  <UserProfile />
  <article>
    <ArticleList />
  </article>
</template>

<script>
import UserProfile from "./components/userProfile";
import ArticleList from "./components/articleList";

export default {
  name: 'App',
  components: {
    UserProfile,
    ArticleList
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
  display: flex;
  flex-flow: column;
  justify-content: center;
  
}
strong {
  margin-top: 16px;
}
</style>
