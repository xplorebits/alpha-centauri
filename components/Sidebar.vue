<template>
  <div class="sidebar">
    <v-list color="transparent">
      <v-list-item>
        <v-list-item-icon>
          <v-avatar :size="24" tile color="yellow" />
        </v-list-item-icon>
        <v-list-item-content>
          <v-list-item-title>
            Aplha Centauri
          </v-list-item-title>
        </v-list-item-content>
      </v-list-item>
    </v-list>
    <v-list color="transparent">
      <template v-for="item in menu">
        <p
          v-if="item.type === 'label'"
          :key="item.id"
          :style="{ color: collapseSidebar ? 'transparent' : 'grey' }"
          class="ma-0 pa-0 px-4 caption"
          v-text="item.text"
        />
        <v-tooltip v-else :key="item.id" :disabled="!collapseSidebar" right>
          <template v-slot:activator="{ on }">
            <v-list-item
              v-if="item.type !== 'label'"
              v-on="on"
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
          <span v-text="item.tip || item.title" />
        </v-tooltip>
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
          id: 'app-sidebar-category-menu',
          text: 'Menu',
          type: 'label'
        },
        {
          id: 'app-sidebar-dashboard',
          title: 'Dashboard',
          icon: 'mdi-view-dashboard',
          tip: 'Your dashboard',
          callback: () => this.$router.push({ path: '/dashboard' })
        },
        {
          id: 'app-sidebar-chat',
          title: 'Chat',
          icon: 'mdi-message-text-outline',
          tip: 'Chat with your team',
          callback: () => this.$router.push({ path: '/chat' })
        },
        {
          id: 'app-sidebar-calendar',
          title: 'Calendar',
          icon: 'mdi-calendar',
          tip: 'View and manage events',
          callback: () => this.$router.push({ path: '/calendar' })
        },
        {
          id: 'app-sidebar-users',
          title: 'Users',
          icon: 'mdi-account-multiple',
          tip: 'View and manage users',
          callback: () => this.$router.push({ path: '/users' })
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
