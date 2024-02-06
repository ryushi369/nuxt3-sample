<template>
  <div>
    <NuxtLayout>
      <NuxtPage />
    </NuxtLayout>
    <h1>{{ title }}</h1>
    <button @click="($event) => titleState.changeTitle('Hello Nuxt3!')">
      Change Title
    </button>
    <ul>
      <li v-for="user in users" :key="user.id">
        {{ user.id }}, {{ user.name }}
      </li>
    </ul>
    <img src="~/assets/mashmelloman.jpeg" alt="mashmelloman" />
  </div>
</template>

<script setup>
const { data: users, error } = await useFetch(
  "https://jsonplaceholder.typicode.com/users"
);

if (error.value) {
  throw createError({ statusCode: 404, statusMessage: "Page not found" });
}

const titleState = useTitle();
const { title } = titleState;

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
