<template>
  @{{ user.username }} - {{ fullName }}
  <strong>Followers: {{ followers }}</strong>
  <button @click="followUser">Add a follower</button>

  <p v-if="!user.isAdmin">This user is a Super user</p>
</template>
  
<script>
  export default {
    name: 'UserProfile',
    data() {
      return {
        followers: 0,
        user: {
          id: 1,
          username: 'Matthy079',
          firstName: "Matthijs",
          lastName: "van der Harst",
          email: "matthijs@fluxility.com",
          isAdmin: true
        }
      }
    },
    watch: {
      followers(newFollowCount, oldFollowCount) {
        if (oldFollowCount < newFollowCount) {
          console.log(`${this.user.username} has gained a follower!`)
        }
      }
    },
    computed: {
      fullName() {
        return `${this.user.firstName} ${this.user.lastName}`;
      }
    },
    methods: {
      followUser() {
        this.followers++
      }
    },
    mounted() {
      this.followUser();
    }
  }
</script>

<style scoped>
strong {
  margin-top: 16px;
}
</style>