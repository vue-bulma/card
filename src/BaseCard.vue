<template>
  <transition
    :name="transition"
    mode="in-out"
    appear
    :appear-active-class="enterClass"
    :enter-active-class="enterClass"
    :leave-active-class="leaveClass"
    @after-leave="afterLeave"
  >
    <div class="card is-fullwidth">
      <header class="card-header">
        <p class="card-header-title">{{ title }}</p>
        <a class="card-header-icon" v-if="!!this.icon">
          <span class="icon">
            <i class="fa" :class="[`fa-${icon}`]"></i>
          </span>
        </a>
      </header>
      <div class="card-content">
        <div class="content">{{ content }}</div>
      </div>
      <footer class="card-footer" v-if="!!this.$slots.footer">
        <slot name="footer"></slot>
      </footer>
    </div>
  </transition>
</template>

<script>
export default {
  props: {
    title: {
      type: String
    },
    icon: String,
    content: String,
    transition: {
      type: String,
      default: 'fade'
    }
  },

  methods: {
    afterLeave () {
      this.$destroy()
    }
  },

  computed: {
    enterClass () {
      return `${this.transition}In`
    },

    leaveClass () {
      return `${this.transition}Out`
    }
  }
}
</script>