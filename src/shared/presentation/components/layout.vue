<script setup>
import {ref} from "vue";
import {Button as PvButton, Menubar as PvMenubar} from "primevue";
import LanguageSwitcher from "./language-switcher.vue";

const drawerVisible = ref(false);
const toggleDrawer = () => {
  drawerVisible.value = !drawerVisible.value;
};
</script>

<template>
<div>
  <div>
    <pv-menubar>
      <template #start>
        <pv-button icon="pi pi-bars" @click="toggleDrawer" label="CatchUp" text/>
        <!-- Add Source List here -->
      </template>
      <template #end>
        <language-switcher/>
      </template>
    </pv-menubar>
  </div>
</div>
</template>

<style scoped>

</style>