<template>
  <button
    class="thl-button"
  >
    <i :class="icon"></i>
  </button>
</template>
<script>
  export default {
    name: 'ThlButton',
    props: {
      icon: {
        type: String,
        default: ''
      },
      disabled: Boolean,

    }
  }
</script>
