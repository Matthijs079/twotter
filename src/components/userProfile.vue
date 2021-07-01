<template>
  @{{ object.username }} - {{ object.fullName }}
  <strong>Followers: {{ object.followers }}</strong>
  <button @click="followUser">Add a follower</button>

  <p v-if="!object.isAdmin">This user is a Super user</p>

  <form class="create-twoot__form" @submit.prevent="createNewTwoot">
    <label class="create-twoot__label" for="newTwootTitle"><strong>New Twoot Title</strong></label>
    <input id="newTwootTitle" v-model="newTwootTitle"/>

    <label class="create-twoot__label" for="newTwootContent"><strong>New Twoot Content</strong></label>
    <textarea id="newTwootContent" rows="4" v-model="newTwootContent"></textarea>

    <div class="create-twoot__type">
      <label class="create-twoot__label" for="newTwootType"><strong>Twoot Type</strong></label>
      <select id="newTwootType" v-model="newTwootType">
        <option v-for="( option, index ) in twootTypes" :key="index" :value="option.value">
          {{ option.name }}
        </option>
      </select>
    </div>

    <button>
      Send Twoot
    </button>
  </form>
</template>
  
<script>
  export default {
    name: 'UserProfile',
    props: ["object"],
    data() {
      return {
        twootTypes: [
          { value: 'draft', name: 'Draft' },
          { value: 'published', name: 'Published' },
        ],
        newTwootTitle: '',
        newTwootContent: '',
        newTwootType: 'published',
      }
    },
    watch: {
      followers(newFollowCount, oldFollowCount) {
        if (oldFollowCount < newFollowCount) {
          console.log(`${this.object.username} has gained a follower!`)
        }
      }
    },
    computed: {
      fullName() {
        return `${this.object.firstName} ${this.object.lastName}`;
      }
    },
    methods: {
      followUser() {
        this.$root.user.followers++
      },

      createNewTwoot() {
        if (this.newTwootContent && this.newTwootType !== 'draft') {
        this.$root.user.twoots.unshift({
          id: this.object.twoots.length + 1,
          title: this.newTwootTitle,
          content: this.newTwootContent,
        }),
        this.newTwootContent = '';
        this.newTwootTitle = '';
      }
      }
    },
    mounted() {
      this.followUser();
    }
  }
</script>

<style lang="scss" scoped>
  strong {
    margin-top: 16px;
  }

  .create-twoot__form {
    display: flex;
    flex-flow: column;
    align-items: flex-start;
    margin: 16px;
  }

  .create-twoot__label {
    margin-bottom: 8px;
  }
</style>