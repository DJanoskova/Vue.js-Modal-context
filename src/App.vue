<template>
  <div id="app">
    <div class="content">
      <Button @click="handleSuccessAlert" class="mr-2">
        Success alert
      </Button>
      <Button @click="handleDangerAlert" class="mr-2">
        Danger alert
      </Button>
      <Button @click="handleSignIn">
        Sign in form
      </Button>
    </div>
    <ModalRoot />
  </div>
</template>

<script>
import { ModalBus } from './eventBus';

import ModalRoot from './components/ModalRoot'
import Button from './components/common/Button'
import SignInForm from './components/examples/SignInForm'
import Alert from './components/examples/Alert';

export default {
  name: 'app',
  components: {
    Button,
    ModalRoot
  },
  methods: {
    handleSuccessAlert () {
      ModalBus.$emit('open', {
        component: Alert,
        props: { text: 'Everything is working great!', type: 'success' }
      })
    },
    handleSignIn () {
      ModalBus.$emit('open', { component: SignInForm, title: 'New group', closeOnClick: false })
    },
    handleDangerAlert () {
      const props = {
        type: 'error',
        text: 'The server returned 500 again! omg!'
      }
      ModalBus.$emit('open', { component: Alert, title: 'An error has occured', props })
    }
  }
}
</script>

<style scoped>
.content {
  width: 100vw;
  height: 100vh;
  display: flex;
  flex-direction: row;
  justify-content: center;
  align-items: center
}
</style>
