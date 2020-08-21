<template>
  <v-app :collapse-sidebar="sidebar.collapse">
    <sidebar :expand="sidebar.expand" :collapse-sidebar="sidebar.collapse" />
    <appbar
      :collapse-sidebar="sidebar.collapse"
      @toggle-sidebar="onToggleSidebar"
    />
    <div class="main-view">
      <nuxt />
    </div>
  </v-app>
</template>

<script>
import Sidebar from '@/components/Sidebar'
import Appbar from '@/components/Appbar'

export default {
  components: {
    Sidebar,
    Appbar
  },
  data() {
    return {
      sidebar: {
        collapse: false
      }
    }
  },
  methods: {
    onToggleSidebar() {
      this.$set(this.sidebar, 'collapse', !this.sidebar.collapse)
    }
  }
}
</script>

<style lang="scss">
::-webkit-scrollbar {
  display: none;
}
#app {
  $sidebarWidth: 256px;
  $sidebarWidthCollapse: 58px;
  $appbarWidth: 48px;

  background-color: #36393f;
  .sidebar {
    background-color: #202225;
    position: fixed;
    top: 0;
    bottom: 0;
    left: 0;
    width: $sidebarWidth;
    transition: all 0.2s ease-in-out;
    z-index: 500;
  }
  .appbar {
    background-color: #36393f;
    border-bottom: 0.5px solid #2a2c31;
    position: fixed;
    top: 0;
    right: 0;
    left: $sidebarWidth;
    height: $appbarWidth;
    transition: all 0.2s ease-in-out;
    z-index: 500;
  }
  .main-view {
    position: fixed;
    top: $appbarWidth;
    right: 0;
    bottom: 0;
    left: $sidebarWidthCollapse;
    overflow-y: auto;
    transition: all 0.2s ease-in-out;
    z-index: 300;
    &::-webkit-scrollbar {
      display: block;
      width: 10px;
    }
    &::-webkit-scrollbar-thumb {
      background-color: #202225;
      border-radius: 10px;
    }
  }
  &[collapse-sidebar] {
    .sidebar {
      width: $sidebarWidthCollapse;
    }
    .appbar {
      left: $sidebarWidthCollapse;
    }
  }
}
</style>
