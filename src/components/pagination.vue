<template>
<nav class="pagination is-right" role="navigation">
  <ul class="pagination-list">
    <li v-show="page > 2">
      <router-link class="pagination-link" aria-label="Goto page 1" to="?_page=1">1</router-link>
    </li>
    <li v-show="totalPage > 5 && page > 3">
      <span class="pagination-ellipsis">&hellip;</span>
    </li>
    <li v-show="page > 1">
      <router-link class="pagination-link" :aria-label="`Goto page ${pagePrev}`" :to="`?_page=${pagePrev}`">{{pagePrev}}</router-link>
    </li>
    <li>
      <a class="pagination-link is-current" :aria-label="`Page ${page}`" aria-current="page" href="javascript:;">{{page}}</a>
    </li>
    <li v-show="page < totalPage">
      <router-link class="pagination-link" :aria-label="`Goto page ${pageNext}`" :to="`?_page=${pageNext}`">{{pageNext}}</router-link>
    </li>
    <li v-show="totalPage > 5 && page < totalPage - 2">
      <span class="pagination-ellipsis">&hellip;</span>
    </li>
    <li v-show="page < totalPage - 1">
      <router-link class="pagination-link" :aria-label="`Goto page ${totalPage}`" :to="`?_page=${totalPage}`">{{totalPage}}</router-link>
    </li>
  </ul>
</nav>
</template>

<script>
import { computed } from 'vue'

export default {
  props: {
    page: Number,
    totalPage: Number
  },
  setup(props) {
    const pagePrev = computed(() => props.page - 1)
    const pageNext = computed(() => props.page + 1)

    return {
      page: props.page,
      totalPage: props.totalPage,
      pagePrev,
      pageNext
    }
  }
}
</script>
