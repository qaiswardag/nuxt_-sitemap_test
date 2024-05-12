<script setup></script>

<template>
  <NuxtLink
    to="/"
    class="text-myPrimaryDarkGrayColor"
  >
    <div class="myPrimaryMenuTextButton">Home</div>
  </NuxtLink>
  <NuxtLink
    to="/listings"
    class="text-myPrimaryDarkGrayColor"
  >
    <div class="myPrimaryMenuTextButton">Listings</div>
  </NuxtLink>
  <a
    href="/sitemap.xml"
    target="_blank"
  >
    Sitemap
  </a>
  <hr />
  <NuxtPage />
</template>
