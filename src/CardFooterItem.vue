<script>
import Vue from 'vue'

const CardFooterItem = Vue.component('card-footer-item', {
  props: {
    element: {
      type: String,
      default: 'a',
      validator: value => ['a', 'link', 'div'].includes(value)
    },
    href: String,
    to: Object
  },

  render (createElement) {
    const { element, href, to } = this
    const dataObj = { 'class': 'card-footer-item' }

    if (element === 'a' && href) {
      dataObj.attrs = { href: href }
    } else if (element === 'link' && to) {
      dataObj.attrs = { to: to }
    }

    if (this.$slots.default) {
      return createElement(element === 'link' ? 'router-link' : element, dataObj, this.$slots.default)
    }
  }
})

export default CardFooterItem
</script>
