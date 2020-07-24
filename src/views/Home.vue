<template>
  <div class="wrap">
    <SideNav />
    <div class="top-nav-pos">
      <TopNav />
      <TopFilterNav />
    </div>
  </div>
</template>

<script>
// @ is an alias to /src
import SideNav from '@/components/core/side-nav.vue';
import TopNav from '@/components/core/top-nav.vue';
import TopFilterNav from '@/components/core/top-filter-nav.vue';

export default {
  name: 'Home',
  components: {
    SideNav,
    TopNav,
    TopFilterNav
  }
}
</script>

<style lang="scss" scoped>
.wrap {
  display: flex;
  flex-direction: row;
}

.top-nav-pos {
  display: flex;
  flex-direction: column;
  width: 90%;
}
</style>
