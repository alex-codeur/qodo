<template>
  <q-layout view="hHh Lpr fFf">
    <q-header elevated>
      <q-toolbar>
        <q-toolbar-title class="absolute-center"> Qodo </q-toolbar-title>
      </q-toolbar>
    </q-header>

    <q-footer elevated>
      <q-tabs>
        <q-route-tab
          v-for="nav in navs"
          :key="nav.label"
          :to="nav.to"
          :icon="nav.icon"
          :label="nav.label"
        />
      </q-tabs>
    </q-footer>

    <q-drawer
      v-model="leftDrawerOpen"
      :breakpoint="767"
      show-if-above
      bordered
      class="bg-primary"
    >
      <q-list dark>
        <q-item-label header> Navigation </q-item-label>

        <q-item
          v-for="nav in navs"
          :key="nav.label"
          :to="nav.to"
          exact
          clickable
          class="text-grey-4"
        >
          <q-item-section avatar>
            <q-icon :name="nav.icon" />
          </q-item-section>

          <q-item-section>
            <q-item-label>{{ nav.label }}</q-item-label>
          </q-item-section>
        </q-item>
      </q-list>
    </q-drawer>

    <q-page-container>
      <router-view />
    </q-page-container>
  </q-layout>
</template>

<script>
import { defineComponent, ref } from "vue";

export default defineComponent({
  name: "MainLayout",
  data() {
    return {
      navs: [
        {
          label: "Todo",
          icon: "list",
          to: "/",
        },
        {
          label: "Settings",
          icon: "settings",
          to: "/settings",
        },
      ],
    };
  },
  setup() {
    const leftDrawerOpen = ref(false);

    return {
      leftDrawerOpen,
      toggleLeftDrawer() {
        leftDrawerOpen.value = !leftDrawerOpen.value;
      },
    };
  },
});
</script>

<style>
@media screen and (min-width: 768px) {
  .q-footer {
    display: none;
  }
}

.q-drawer .q-router-link-exact-active {
  color: white !important;
}
</style>