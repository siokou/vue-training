<template>
  <div id="app">
    <h1>{{title}}</h1>
    <Navbar />
    <Blogs />
    <AllFriends :friends="friends" @delete="deleteFriend" />
    <OnlineFriends :friends="friends" />
  </div>
</template>

<script>
import Navbar from './Navbar'
import AllFriends from './AllFriends'
import OnlineFriends from './OnlineFriends'
import Blogs from './Blogs'

export default {
  name: 'app',
  components: {
    Navbar: Navbar,
    AllFriends: AllFriends,
    OnlineFriends: OnlineFriends,
    Blogs: Blogs
  },
  data () {
    return {
      title: 'My first Vue app, wooo :)',
      friends: [
        { name: "Mario", online: true },
        { name: "Luigi", online: false },
        { name: "Toad", online: true },
        { name: "Bowser", online: false }
      ]		      
    }
  },
  methods: {
    deleteFriend(payload) {
      console.log(payload);
      this.friends = this.friends.filter(friend => {
        return friend.name !== payload.name 
      })
    }
  }
}
</script>

<style lang="scss">
h1 {
  color: #444;
  font-weight: normal;
  text-align: center;
}
</style>
