<template>
  <div class="welcome container">
    <div v-if="showLogin">
      <h2>Login to the chatroom</h2>
      <LoginForm @login="handleEnterChat" />
      <p>No account yet? <span @click="showLogin = !showLogin">Sign up</span></p>
    </div>
    <div v-else>
      <h2>Sign up to the chatroom</h2>
      <SignupForm @signup="handleEnterChat" />
      <p>Already registered? <span @click="showLogin = !showLogin">Login</span></p>
    </div>
  </div>
</template>

<script>
import { ref } from 'vue'
import { useRouter } from 'vue-router'
import SignupForm from '../components/SignupForm'
import LoginForm from '../components/LoginForm'

export default {

  components: {
    SignupForm,
    LoginForm,
  },

  setup() {
    const showLogin = ref(true)
    const router = useRouter()
    const handleEnterChat = () => {
      router.push({ name: 'ChatRoom' })
    }

    return { showLogin, handleEnterChat }
  }
}
</script>

<style>
.welcome {
  text-align: center;
  padding: 20px 0;
}

.welcome form {
  width: 300px;
  margin: 20px auto;
}

.welcome label {
  display: block;
  margin: 20px 0 10px;
}

.welcome input {
  width: 100%;
  padding: 10px;
  border-radius: 6px;
  border: 1px solid #eee;
  outline: none;
  color: #999;
  margin: 10px auto;
  box-sizing: border-box;
}

.welcome span{
  font-weight: bold;
  text-decoration: underline;
  cursor: pointer;
}

.welcome button {
  margin: 20px auto;
  cursor: pointer;
}
</style>