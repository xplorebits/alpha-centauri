<template>
  <div class="sidebar">
    <v-list color="transparent">
      <template v-for="item in menu">
        <v-list-item
          v-if="item.type !== 'label'"
          :key="item.id"
          @click="item.callback"
        >
          <v-list-item-icon>
            <v-icon v-text="item.icon" />
          </v-list-item-icon>
          <v-list-item-content>
            <v-list-item-title v-text="collapseSidebar ? '' : item.title" />
          </v-list-item-content>
        </v-list-item>
      </template>
    </v-list>
  </div>
</template>

<script>
export default {
  props: {
    collapseSidebar: {
      type: Boolean,
      required: true,
      default: () => false
    }
  },
  data() {
    return {
      menu: [
        {
          id: 'app-sidebar-dashboard',
          title: 'Dashboard',
          icon: 'mdi-view-dashboard',
          callback: () => {}
        },
        {
          id: 'app-sidebar-dashboard',
          title: 'Dashboard',
          icon: 'mdi-view-dashboard',
          callback: () => {}
        },
        {
          id: 'app-sidebar-category-apps',
          label: 'APPS',
          type: 'label'
        }
      ]
    }
  }
}
</script>
