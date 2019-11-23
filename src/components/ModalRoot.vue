<template>
  <component :is="modalType" :isOpen="!!component" :title="title" @onClose="handleModalClose">
    <component :is="component" @onClose="handleClose" v-bind="props" />
  </component>
</template>

<script>
import { ModalBus } from '../eventBus'
import FadeInModal from './common/modals/FadeInModal'
import SimpleModal from './common/modals/SimpleModal'

const defaultModal = 'FadeInModal';

export default {
  data () {
    return {
      component: null,
      title: '',
      props: null,
      closeOnClick: true,
      modalType: defaultModal
    }
  },
  created () {
    ModalBus.$on('open', ({ modalType, component, title = '', props = null, closeOnClick = true }) => {
      this.modalType = modalType || defaultModal
      this.component = component
      this.title = title
      this.props = props
      this.closeOnClick = closeOnClick
    })
    document.addEventListener('keyup', this.handleKeyup)
  },
  beforeDestroy () {
    document.removeEventListener('keyup', this.handleKeyup)
  },
  methods: {
    handleModalClose (force = false) {
      if (!this.closeOnClick && !force) return
      this.handleClose()
    },
    handleClose () {
      this.component = null
    },
    handleKeyup (e) {
      if (e.keyCode === 27) this.handleClose()
    }
  },
  components: { 
    SimpleModal,
    FadeInModal   
  }
}
</script>
