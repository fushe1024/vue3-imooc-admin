<script setup>
import SideBar from './components/SideBar'
import NavBar from './components/NavBar.vue'
import AppMain from './components/AppMain.vue'
import TagsView from '@/components/TagsView/index.vue'
import { useStore } from 'vuex'
const store = useStore()
</script>

<template>
  <div
    class="app-wrapper"
    :class="[store.getters.sidebarOpend ? 'openSidebar' : 'hideSidebar']"
  >
    <!-- side-bar -->
    <side-bar
      id="guide-sidebar"
      class="sidebar-container"
      :style="{ backgroundColor: store.getters.cssVar.menuBg }"
    ></side-bar>
    <div class="main-container">
      <div class="fixed-header">
        <!-- navbar -->
        <nav-bar></nav-bar>
        <!-- tags-view -->
        <tags-view id="guide-tags"></tags-view>
      </div>
      <!-- main -->
      <app-main></app-main>
    </div>
  </div>
</template>

<style scoped lang="scss">
@import '~@/styles/mixin.scss';
@import '~@/styles/variables.module.scss';

.app-wrapper {
  @include clearfix;
  position: relative;
  height: 100%;
  width: 100%;
}

.fixed-header {
  position: fixed;
  top: 0;
  right: 0;
  z-index: 9;
  width: calc(100% - #{$sideBarWidth});
  transition: width 0.28s;
}

.hideSidebar .fixed-header {
  width: calc(100% - #{$hideSideBarWidth});
}
</style>
