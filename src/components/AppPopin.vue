<template>
  <transition name="fade">
    <div v-if="show" class="fixed top-0 left-0 right-0 bottom-0 z-50 flex items-center justify-center">
      <div class="bg-black opacity-30 h-full w-full absolute" style="z-index: -1" @click="close"></div>
      <div class="bg-gray w-full max-w-lg rounded-md m-2">
        <div class="shadow-sm p-2 text-dark-gray">
          <div class="float-right">
            <XIcon
              class="cursor-pointer h-8 w-8"
              @click.prevent="close"
            />
          </div>
          <h1 class="text-xl text-center">
            {{ title }}
          </h1>
        </div>
        <slot></slot>
      </div>
    </div>
  </transition>
</template>

<script>
import { XIcon } from '@heroicons/vue/outline'

export default {
  name: 'AppPopin',
  props: {
    show: {
      type: Boolean,
      default: false
    },
    title: {
      type: String,
      require: true
    }
  },
  methods: {
    close () {
      this.$emit('close')
    }
  },
  components: {
    XIcon
  }
}
</script>

<style lang="scss">
.fade-enter-active,
.fade-leave-active {
  transition: opacity 0.5s ease;
}

.fade-enter-from,
.fade-leave-to {
  opacity: 0;
}
</style>