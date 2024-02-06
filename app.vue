<template>
  <div>
    <NuxtLayout>
      <NuxtPage />
    </NuxtLayout>
    <ul>
      <li v-for="user in users" :key="user.id">
        {{ user.id }}, {{ user.name }}
      </li>
    </ul>
  </div>
</template>

<script setup>
const { data: users, error } = await useFetch(
  "https://jsonplaceholder.typicode.com/users"
);

if (error.value) {
  throw createError({ statusCode: 404, statusMessage: "Page not found" });
}

useHead({
  title: "Nuxt3 Sample Store",
  link: [
    {
      rel: "stylesheet",
      href: "https://fonts.googleapis.com/css2?family=Permanent+Marker&display=swap",
    },
  ],
});
</script>
