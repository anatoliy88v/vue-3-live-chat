<template>
  <div class="container">
    <Navbar />
    <ChatWindow />
    <NewChatForm />
  </div>
</template>

<script>
import { watch } from 'vue'
import getUser from '../composables/getUser'
import { useRouter } from 'vue-router'
import Navbar from '../components/Navbar'
import NewChatForm from '../components/NewChatForm'
import ChatWindow from '../components/ChatWindow'

export default {

  components: {
    Navbar,
    NewChatForm,
    ChatWindow,
  },

  setup(props, context) {
    const router = useRouter()
    const { user } = getUser()

    watch(user, () => {
      if (!user.value) {
        router.push({ name: 'Welcome' })
      }
    })
  }
}
</script>