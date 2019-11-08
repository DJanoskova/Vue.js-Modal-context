<template>
  <transition name="fade">
    <div class="modal-backdrop"
      v-show="isOpen"
      :class="{open: isOpen}"
      @click="$emit('onClose')">

      <div class="modal-dialog" :class="{open: isOpen}" @click.stop>
        <div class="modal-title" v-if="title">{{ title }}</div>
        <div class="modal-body">
          <slot />
        </div>
      </div>

    </div>
  </transition>
</template>

<script>
export default {
  props: {
    isOpen: Boolean,
    title: String
  }
}
</script>

<style scoped>
.fade-enter-active, .fade-leave-active {
  transition: 0.5s;
}

.fade-enter, .fade-leave-to {
  opacity: 0;
}

.fade-enter .modal-dialog, .fade-leave-to .modal-dialog {
  transform: translateY(-20%);
}

.modal-backdrop {
  background: rgba(250, 250, 250, 0.8);
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  display: flex;
  flex-direction: row;
  justify-content: center;
  align-items: center
}

.modal-dialog {
  width: 30rem;
  background: rgb(255, 255, 255);
  padding: 1.5rem 2rem;
  box-shadow: 0 10px 15px -3px rgba(0, 0, 0, 0.1), 0 4px 6px -2px rgba(0, 0, 0, 0.05);
  border-radius: 0.3rem;
  transition: 0.5s;
}

.modal-title {
  font-weight: bold;
  font-size: 1.3rem;
  margin-bottom: 1rem;
  color: rgb(100, 100, 100);
}

.modal-body {
  color: rgb(180, 180, 180);
}
</style>
