<script>
import axios from 'axios'
import ChatBoard from '@/components/ChatBoard.vue'
import UserCard from '@/components/UserCard.vue'
export default {
  name: 'MensajeriaComponent',
  components: {
    ChatBoard,
    UserCard
  },
  data() {
    return {
      userLeft: {},
      userRight: {},
      messages: []
    }
  },
  async created() {
    try {
      const url = 'https://randomuser.me/api/?results=2'
      const { data } = await axios.get(url)

      this.userLeft = data.results[0]
      this.userRight = data.results[1]
    } catch (error) {
      console.error(error)
    }
  }
}
</script>
<template>
  <h1>Chat Mazinger</h1>

  <div class="chat-app-container container">
    <UserCard :user="userLeft" />
    <ChatBoard />
    <UserCard :user="userRight" />
  </div>
</template>
