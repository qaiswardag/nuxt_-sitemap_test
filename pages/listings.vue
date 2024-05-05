<script setup>
import { onMounted } from 'vue';
import TailwindPagination from '../TailwindPagination';

const stores = ref(null);
const getData = async function (pageNumber) {
  const url = `http://localhost:8000/api/guest/stores/index?page=${pageNumber}`;

  const res = await fetch(url);
  stores.value = await res.json();
  console.log(`stores:`, stores.value);
};

const getResultsForPage = (page = 1) => {
  getData(page);
};

onMounted(() => {
  getData(1);
});
</script>

<template>
  <NuxtPage />

  <div class="border-2 border-red-200 p-4 m-4">
    <template v-if="stores && stores.posts && stores.posts.data">
      <div class="py-12">
        <div
          v-for="item in stores.posts.data"
          :key="item.id"
        >
          <p class="py-4">Title: {{ item.title }}</p>
        </div>
      </div>
    </template>
    <template v-if="stores && stores.posts">
      <TailwindPagination
        :limit="1"
        :keepLength="true"
        :active-classes="[
          'bg-myPrimaryLinkColor',
          'text-white',
          'rounded-full',
        ]"
        :item-classes="[
          'p-0',
          'm-0',
          'border-none',
          'bg-myPrimaryLightGrayColor',
          'shadow-sm',
          'hover:bg-gray-300',
          'text-myPrimaryDarkGrayColor',
          'rounded-full',
        ]"
        :data="stores.posts"
        @pagination-change-page="getResultsForPage"
      >
        <template #prev-nav>
          <span> Prev </span>
        </template>
        <template #next-nav>
          <span>Next</span>
        </template>
      </TailwindPagination>
    </template>
  </div>
</template>
