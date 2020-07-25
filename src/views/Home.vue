<template>
  <div class="wrap">
    <SideNav />
    <div class="top-nav-pos">
      <TopNav />
      <TopFilterNav />
      <div class="main-screen">
        <div class="el-wrap">
          <img src="../assets/img-audit-noresults.png" alt="No Result Found" />
          <h3>Nothing to Show</h3>
          <h4>To see audit logs, choose the filters and/or <br>perform a search from the above menu.</h4>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
// @ is an alias to /src
import SideNav from "@/components/core/side-nav.vue";
import TopNav from "@/components/core/top-nav.vue";
import TopFilterNav from "@/components/core/top-filter-nav.vue";

export default {
  name: "Home",
  components: {
    SideNav,
    TopNav,
    TopFilterNav,
  },
};
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

.main-screen {
  background-color: #F4F4F4;
  height: 100%;
  position: relative;
  z-index: 1;
  .el-wrap {
    position: absolute;
    top: 30%;
    left: 35%;
    h3 {
      margin-bottom: 5px;
    }
    h4 {
      font-weight: 500;
      margin: 0;
    }
  }
}
</style>
