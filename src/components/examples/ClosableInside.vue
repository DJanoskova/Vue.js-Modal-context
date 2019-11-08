<template>
  <div>
    <p class="mb-4">
      This dialog is closable from the inside of the component!
    </p>
    <div class="text-right">
      <Button @click="$emit('onClose')" color="gray">Close</Button>
    </div>
  </div>
</template>

<script>
import Button from '../common/Button';

export default {
  components: { Button }
}
</script>
