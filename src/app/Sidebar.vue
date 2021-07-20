<template>
  <div class="sidebar-container elevated">
    <div class="sidebar-fixed d-none d-md-block">
      <Nav />
    </div>
    <b-sidebar
      :visible="showMenu"
      class="d-md-none"
      sidebar-class="elevated"
      bg-variant=""
      shadow="lg"
      no-header
      backdrop
      backdrop-variant=""
      @hidden="hideMenu"
    >
      <Nav />
    </b-sidebar>
  </div>
</template>
<style lang="scss">
.sidebar-container {
  .nav {
    overflow-y: auto;
    scrollbar-width: thin;
    scrollbar-color: white transparent;
    max-height: 100vh;
    padding-bottom: 80px;
    flex-wrap: nowrap;
  }
  .sidebar-fixed {
    position: sticky;
    top: 0;
    padding-left: 0.5rem;
    padding-right: 0.5rem;
    width: 250px;
  }
  .sidebar-brand {
    padding: 1rem 1rem 0.75rem;
  }
  .sidebar-heading {
    padding: 0.5rem 1rem;
    font-weight: bold;
    text-transform: uppercase;
    display: block;
  }

  a.nav-link {
    flex-shrink: 0;
    width: calc(100%);
    overflow: hidden;
    text-overflow: ellipsis;
    white-space: nowrap;
    .b-icon {
      margin-right: 0.75rem;
    }
    &:not(.router-link-active) .b-icon {
      color: var(--text-muted);
    }
    &:hover {
      color: inherit;
      background-color: rgba(255, 255, 255, 0.045);
    }
    &.router-link-active {
      color: var(--primary);
      background-color: rgba(255, 255, 255, 0.045);
      &:hover {
        color: var(--primary);
      }
    }
  }
}
</style>
<script lang="ts">
import Vue from "vue";
import Nav from "./Nav.vue";
import { mapState, mapActions } from "vuex";

export default Vue.extend({
  components: {
    Nav,
  },
  computed: {
    ...mapState(["showMenu"]),
  },
  methods: {
    ...mapActions(["hideMenu"]),
  },
});
</script>
