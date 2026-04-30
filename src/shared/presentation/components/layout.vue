<script setup>
import {ref, onMounted} from "vue";
import axios from "axios";

import LanguageSwitcher from "./language-switcher.vue";
import FooterContent from "./footer-content.vue";
import {Card as PvCard, Drawer as PvDrawer} from "primevue";

const drawerVisibe = ref(false);
const toggleDrawer = () => {
  drawerVisibe.value = !drawerVisibe.value;
};
const data = ref([])
onMounted(async () => {
  const res = await axios.get('http://universities.hipolabs.com/search?country=peru');
  data.value = res.data;

});

/*
const fetchAPI = async() =>{
  const response=await fetch('http://universities.hipolabs.com/search?country=peru');
  const data=await response.json();
  console.log(data[0]);
  return data;
}
fetchAPI();
*/

</script>

<template>
  <div>
    <div>
      <pv-menubar>
        <template #start>
          <pv-button icon="pi pi-bars" @click="toggleDrawer" label="Catchar" text/>
          <!-- Add source list here-->
        </template>
        <template #end>
          <language-switcher/>
        </template>
      </pv-menubar>
    </div>
  </div>
  <div>
    <pv-card v-for="da in data"
             :key="da.name">
      <template #header>
        <img
            :src="'https://img.logo.dev/'+da.domains[0]+'?token=pk_NVVbyuM_RkCABhzvFnmxMQ'"
            alt="logo"
        />
      </template>
      <template #title> {{da.country}}
      <hr>
      </template>

    </pv-card>
    <!-- Logo -->
    <div v-if="drawerVisibe" class="flex justify-center my-4">
      <img
          src="https://img.logo.dev/stripe.com?token=pk_NVVbyuM_RkCABhzvFnmxMQ"
          alt="Stripe logo"
          class="w-24 h-24 object-contain rounded-xl shadow-md bg-white p-2"
      />
    </div>
    <li
        v-for="da in data"
        :key="da.name"
        class="flex justify-between items-center p-3 rounded-lg shadow-sm border border-gray-100 hover:shadow-md transition"
    >
      <div class="font-bold">
        {{ da.country }}
      </div>

      <div class="text-2xl">
        {{ da.name }}
      </div>
      <div>
        {{da.domains[0]}}
      </div>
    </li>
    <!-- Listar
    <ul class="space-y-3 px-4">
      <li
          v-for="da in data"
          :key="da.name"
          class="flex justify-between items-center p-3 rounded-lg shadow-sm border border-gray-100 hover:shadow-md transition"
      >
        <div class="font-bold">
          {{ da.country }}
        </div>

        <div class="text-2xl">
          {{ da.name }}
        </div>
        <div>
          {{da.domains[0]}}
        </div>
      </li>
    </ul>
    -->
    <!-- FORMATO CARDDDDDDDDDDDDDDDDDDDDDDDDDDDDDDDDDDD
    <Card style="width: 25rem; overflow: hidden">
    <template #header>
        <img alt="user header" src="/images/usercard.png" />
    </template>
    <template #title>Advanced Card</template>
    <template #subtitle>Card subtitle</template>
    <template #content>
        <p class="m-0">
            Lorem ipsum dolor sit amet, consectetur adipisicing elit. Inventore sed consequuntur error repudiandae numquam deserunt quisquam repellat libero asperiores earum nam nobis, culpa ratione quam perferendis esse, cupiditate neque
            quas!
        </p>
    </template>
    <template #footer>
        <div class="flex gap-4 mt-1">
            <Button label="Cancel" severity="secondary" variant="outlined" class="w-full" />
            <Button label="Save" class="w-full" />
        </div>
    </template>
</Card>
-->
  </div>
  <footer-content/>
</template>

<style scoped>

</style>