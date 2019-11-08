<template>
  <div id="app">
    <div class="content">
      <Button @click="openSuccessAlert" class="mr-2">
        Success alert
      </Button>
      <Button @click="openDangerAlert" class="mr-2">
        Danger alert
      </Button>
      <Button @click="openClosableInside" class="mr-2">
        Close from inside
      </Button>
      <Button @click="openSignIn">
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
import ClosableInside from './components/examples/ClosableInside';

export default {
  name: 'app',
  components: {
    Button,
    ModalRoot
  },
  methods: {
    openSuccessAlert () {
      ModalBus.$emit('open', {
        component: Alert,
        props: { text: 'Everything is working great!', type: 'success' }
      })
    },
    openDangerAlert () {
      const props = {
        type: 'error',
        text: 'The server returned 500 again! omg!'
      }
      ModalBus.$emit('open', { component: Alert, title: 'An error has occured', props })
    },
    openClosableInside () {
      ModalBus.$emit('open', { component: ClosableInside, title: 'Close dialog from component' })
    },
    openSignIn () {
      ModalBus.$emit('open', { component: SignInForm, title: 'New user', closeOnClick: false })
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
