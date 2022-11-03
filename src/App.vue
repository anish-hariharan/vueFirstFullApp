<template>
  <section>
    <header>
      <h1>My Friends</h1>
    </header>
    <new-friend @add-contact="addContact"></new-friend>
    <ul>
      <friend-contact
        v-for="friend in friends"
        :id="friend.id"
        :key="friend.id"
        :name="friend.name"
        :phone-number="friend.phone"
        :email-a="friend.email"
        :is-favourite="friend.fav"
        :is-visible="friend.vis"
        @toggle-favourite="toggleFavouriteStatus"
        @visible="visibleData"
        @delete="deleteContact"
      ></friend-contact>
    </ul>
  </section>
</template>

<script>
import FriendContact from "./components/FriendContact.vue";
export default {
  components: { FriendContact},
  data() {
    return {
      friends: [
        {
          id: "anish",
          name: "Anish Hariharan",
          phone: "123 456 789",
          email: "anish@gmail.com",
          fav: false,
          vis: false
        },
        {
          id: "tiger",
          name: "Tiger",
          phone: "123 456 789",
          email: "anishT@gmail.com",
          fav: false,
          vis: false
        },
      ],
    };
  },
  methods: {
    toggleFavouriteStatus(friendId) {
      const identifiedFriend = this.friends.find(friend => friend.id === friendId)
      identifiedFriend.fav = !identifiedFriend.fav
    },
    addContact(name, phone, email) {
      const newFriend = {
        id: new Date().toISOString(),
        name : name,
        phone : phone,
        email : email,
        fav: false
      }
      this.friends.push(newFriend)
    },
    visibleData(id){
      const friend = this.friends.find(friend => friend.id === id)
      friend.vis = !friend.vis
      console.log(this.friends)
    },
    deleteContact(id){
      const friend = this.friends.find(friend => friend.id === id)
      let index = this.friends.indexOf(friend)
      index === 0 ? this.friends.shift() : this.friends.splice(index, index)
      console.log(this.friends)
    }
  },
};
</script>

<style>
* {
  box-sizing: border-box;
}

html {
  font-family: "Jost", sans-serif;
}

body {
  margin: 0;
}

header {
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.26);
  margin: 3rem auto;
  border-radius: 10px;
  padding: 1rem;
  background-color: #58004d;
  color: white;
  text-align: center;
  width: 90%;
  max-width: 40rem;
}

#app ul {
  margin: 0;
  padding: 0;
  list-style: none;
}

#app li,
#app form {
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.26);
  margin: 1rem auto;
  border-radius: 10px;
  padding: 1rem;
  text-align: center;
  width: 90%;
  max-width: 40rem;
}

#app h2 {
  font-size: 2rem;
  border-bottom: 4px solid #ccc;
  color: #58004d;
  margin: 0 0 1rem 0;
}

#app button {
  font: inherit;
  cursor: pointer;
  border: 1px solid #ff0077;
  background-color: #ff0077;
  color: white;
  padding: 0.05rem 1rem;
  box-shadow: 1px 1px 2px rgba(0, 0, 0, 0.26);
}

#app button:hover,
#app button:active {
  background-color: #ec3169;
  border-color: #ec3169;
  box-shadow: 1px 1px 4px rgba(0, 0, 0, 0.26);
}

#app input {
  font: inherit;
  padding: 0.15rem;
}
#app label{
  font-weight: bold;
  margin-right: 1rem;
  width: 7rem;
  display: inline-block;
}
#app form div {
  margin: 1rem 0;
}
</style>
