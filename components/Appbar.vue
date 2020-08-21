<template>
  <div class="appbar">
    <div class="d-flex align-center px-2" style="height: 100%;">
      <v-btn icon text @click="onClickToggleSidebar">
        <v-icon>
          {{ collapseSidebar ? 'mdi-menu-right' : 'mdi-menu-left' }}
        </v-icon>
      </v-btn>
      <v-spacer />
      <v-avatar size="32" color="yellow" @click="() => {}" />
    </div>
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
  methods: {
    onClickToggleSidebar() {
      this.$emit('toggle-sidebar')
    }
  }
}
</script>
