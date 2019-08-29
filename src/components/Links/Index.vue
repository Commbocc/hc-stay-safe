<template lang="html">
  <div class="card mb-3">
    <div class="card-header" :class="header">
      <h4 class="card-title text-center" :class="header">
        {{ title }}
      </h4>
    </div>

    <ul class="nav flex-column mb-0">
      <li v-for="(link, i) in links" class="nav-item" :key="i">
        <a is="Link" :link="link" class="nav-link"></a>
        <hr class="m-0">
      </li>
    </ul>
  </div>
</template>

<script>
import Link from './Link'

export default {
  props: {
    title: {
      type: String,
      requried: true
    },
    header: {
      type: String
    }
  },
  components: {
    Link
  },
  computed: {
    links () {
      return (this.$slots.default) ? this.$slots.default.filter(x => x.tag === 'a' && x.data && x.children) : []
    }
  }
}
</script>
