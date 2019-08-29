<script>
import * as components from './components'

export default {
  name: 'app',
  install (Vue) {
    Vue.mixin({
      components: {
        ...components
      }
    })
  }
}
</script>

<style></style>
