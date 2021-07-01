<template>
  <h1>Twotter</h1>
  <div class="container">
    <aside class="user-profile">
      <UserProfile :object="user" />
    </aside>
    <article>
      <ArticleList :object_list="user.twoots" />
    </article>
  </div>
</template>

<script>
import UserProfile from "./components/UserProfile";
import ArticleList from "./components/ArticleList";

export default {
  name: 'App',
  components: {
    UserProfile,
    ArticleList
  },
  data () {
    return {
      user: {
        id: 1,
        username: 'Matthy079',
        firstName: "Matthijs",
        lastName: "van der Harst",
        email: "matthijs@fluxility.com",
        isAdmin: true,
        followers: 0,
        twoots: [
          {
            id: 1,
            content: "Matthijs is amazing",
            title: "Matthijs is awesome"
          },
          {
            id: 2,
            content: "This is my second twoot",
            title: "twotter"
          }
        ]
      },
    }
  },
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
  display: flex;
  flex-flow: row wrap;
  justify-content: center;
}

.container {
  display: flex;
  flex-flow: row nowrap;
  /* justify-content: space-between; */
  max-width: 1280px;
  margin: 0 auto;
  width: 100%;
}

h1 {
  width: 100%;
  margin-bottom:40px;
}
strong {
  margin-top: 16px;
}
article{
  width: 100%;
  max-width: 980px;
  margin-left: 40px;
  background-color: #f3f3f3;
}

.list__inner {
  display: flex;
  flex-flow: column wrap;
}

.list__item {
  border-bottom: 3px solid grey;
  background-color: lightgray;
  padding: 16px 32px;
  margin: 16px;
  box-sizing: border-box;
}

.user-profile {
  width: 100%;
  max-width: 300px;
  box-shadow: 0 0 16px 0 #E8E8E8;
  display: flex;
  flex-flow: column wrap;
}

</style>
