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
      </header>
      <div class="card-content">
        <div class="content">{{ content }}</div>
      </div>
      <footer class="card-footer">
        <a class="card-footer-item" :href="action.href" v-if="action.href" v-for="action in actions">
          <span class="icon is-small" v-if="action.icon">
            <i class="fa" :class="[`fa-${action.icon}`]" aria-hidden="true"></i>
          </span>&nbsp;&nbsp;
          {{ action.text }}
        </a>
        <a class="card-footer-item" @click="action.click" v-if="action.click" v-for="action in actions">
          <span class="icon is-small" v-if="action.icon">
            <i class="fa" :class="[`fa-${action.icon}`]" aria-hidden="true"></i>
          </span>&nbsp;&nbsp;
          {{ action.text }}
        </a>
        <router-link class="card-footer-item" :to="{ name: action.name }" v-if="action.name" v-for="action in actions">
          <span class="icon is-small" v-if="action.icon">
            <i class="fa fa-link" :class="[`fa-${action.icon}`]" aria-hidden="true"></i>
          </span>&nbsp;&nbsp;
          {{ action.text }}
        </router-link>
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
    content: String,
    actions: {
      type: Array,
      default: () => {
        return [{
          text: 'OK',
          icon: 'check',
          click: () => { console.log('OK clicked') }
        }]
      }
    },
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